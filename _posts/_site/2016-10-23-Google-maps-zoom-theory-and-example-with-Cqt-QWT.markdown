= Google maps zoom theory and example with {C++/qt ; QWT}
:hp-tags: c++, qwt plot, qt, zoom, google maps
:hp-image: /images/qwt_plot.png

===== Theory

Recently I had to set up a zoom on a qwt plot, the goal was to get the same zoom as google maps when zooming on some coordinates. 

qwt plot example :

image:qwt_plot.png[qwt plot, 500, 500, align="center"]

Open maps and test, put your cursor on a city and zoom, all the map will be zoomed but the city will always be under your cursor. 

The solution is easy, the main idea is to reset your scales with a factor (ex : 0.9 or 1.1) and to apply a part of the factor by using the position of the cursor in order to get the zoom or unzoom. 

We will assume that the x axis is the horizontal and y the vertical.
So if we want to zoom on the point which is at (1, 2.5)  [(x, y)] we will :

- get the position of our cursor on the widget (x_cursor, y_cursor)
- define the percentage (x_percent, y_percent) which are the percentage of the x_cursor position and the x_cursor_max position (size max of the widget) and the same for y_percent with y_cursor and y_cursor_max.
- we will compute the new x scale with x_percent of the factor on a side and 100 - x_percent of the factor for the other side and do the same for the y scale with y_percent / the factor.

After processing all of this we will have the x axis scale [0.2, 4] and the y axis scale [0.4, 8.5].


==== Code with c++/qt and qwt library : 


This code is based on the *PlotMagnifier::rescale(double factor);* function.

[source,cpp]
----
void My_PlotMagnifier::rescale_on_cursor(double factor,      // the rescale factor (0.9 or 1.1)
                                         int x_cursor,       // the x, y position of the cursor
                                         int y_cursor,
                                         QSize parent_size)  // the max size of the widget
{
    QwtPlot* plt = plot();

    // max size of the widget
    float x_cursor_max = parent_size.width();
    float y_cursor_max = parent_size.height();

    // percentage position of the cursor in the widget
    float x_percent = (x_cursor * 100) / x_cursor_max;
    float y_percent = (y_cursor * 100) / y_cursor_max;

    // will be the new lowerBound and upperBound of the scales
    float delta_1 = 0;
    float delta_2 = 0;

    _plotScaleEngine->zoomed(true);
    bool doReplot = false;
    const bool autoReplot = plt->autoReplot();
    plt->setAutoReplot( false );

    for ( int axisId = 0; axisId < QwtPlot::axisCnt; axisId++ )
    {
        const QwtScaleDiv &scaleDiv = plt->axisScaleDiv( axisId );
        if ( isAxisEnabled( axisId ) )
        {
            double center = scaleDiv.lowerBound() + scaleDiv.range() / 2;	// Here we set the center of the scale
            const double width_2 = scaleDiv.range() / 2 * factor;			// the width wanted between lowerBound (or upper) and the center
            float interval = (scaleDiv.range() / 2) - width_2;				// the interval between the old width and the wanted width

            if (axisId == 0) 		// y - left
            {
                delta_1 = (center - width_2) + (((100 - y_percent) * interval) / 100) - interval;
                delta_2 = (center + width_2) - ((y_percent * interval) / 100) + interval;
            }
            else if (axisId == 2) 	// x - bottom
            {
                delta_1 = (center - width_2) + (((x_percent * interval) / 100)) - interval;
                delta_2 = (center + width_2) - (((100 - x_percent) * interval) / 100) + interval;
            }
            else
            {
                delta_1 = 0;
                delta_2 = 0;
            }
            plt->setAxisScale(axisId, delta_1, delta_2);
            doReplot = true;
        }
    }
    plt->setAutoReplot( autoReplot );
    if ( doReplot )
        plt->replot();
}

void Gr_PlotMagnifier::widgetWheelEvent(QWheelEvent *WheelEvent)
{
    _plotScaleEngine->getPlot()->select();
    QSize parent_size = this->parentWidget()->size();

    if (WheelEvent->delta() > 0) 	// unzoom
        rescale_on_cursor(0.9, WheelEvent->x(), WheelEvent->y(), parent_size);
    else 							// zoom
        rescale_on_cursor(1.1, WheelEvent->x(), WheelEvent->y(), parent_size);
}



----






