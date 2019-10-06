= Spacemacs
// See https://hubpress.gitbooks.io/hubpress-knowledgebase/content/ for information about the parameters.
// :hp-image: /covers/cover.png
// :published_at: 2019-01-31
// :hp-tags: HubPress, Blog, Open_Source,
// :hp-alt-title: My English Title




# Org


## categories

    void process_stuff(my_super_class* ptr);
    
    int a = 2;

    def example(a, b):
       """
       in a src block use ctrlc ' (ctrlc + single quote) to edit the code block in editor
       use ctrlc ctrlc to evaluate it and made appear the results (but doesn't work for now)
       """
       print ("will process {} + {}".format(a, b))
       return (a,b)
    
    example(2, 18)


## Commands

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">command</th>
<th scope="col" class="org-left">action</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">shift tab</td>
<td class="org-left">changes  fold</td>
</tr>


<tr>
<td class="org-left">ctrlc and wait</td>
<td class="org-left">all the commands with description will displayed</td>
</tr>


<tr>
<td class="org-left">ctrlc ctrle</td>
<td class="org-left">export file</td>
</tr>


<tr>
<td class="org-left">ctrlc ctrlc</td>
<td class="org-left">compute part</td>
</tr>


<tr>
<td class="org-left">ctrlc ctrlt</td>
<td class="org-left">cycle through TODO states</td>
</tr>


<tr>
<td class="org-left">ctrlc ctrld</td>
<td class="org-left">add a deadline to a TODO element</td>
</tr>


<tr>
<td class="org-left">ctrlc ctrls</td>
<td class="org-left">append a datetime</td>
</tr>
</tbody>
</table>


## SPC commands

spc mee    - export in different kind of files


## Todo & cie


### TODO todo example

at the end of the title line (after example here) hit shift alt enter
to go to the next line with another todo
use ctrlc ctrld to add a deadline do a todo element

1.  under task one.
2.  [ ] under task two.
3.  [ ] 


### DONE clycle through states

use ctrlc ctrlt tou cylcle through states


### use list <code>[1/2]</code>

use ctrlc ctrlc on one line to set or unset the state

-   [ ] task one
-   [X] task two


### use other list <code>[50%]</code>

-   [ ] item one
-   [X] item two


## Schedules

use ctrlc ctrls to append a datetime
move cursor on the datetime and use shift left / right to change the value


## commands (spc spc my<sub>super</sub><sub>command</sub>)

org-md-export-to-markdown     - export to a text file with markdown syntax (my<sub>file.md</sub>)


## LaTex integration

-   Characters: &alpha; &rarr; &beta;
-   \(O(n \log n)\)

\begin{align*}
  3 * 2 + 1 &= 6 + 1\\
           &= 7
\end{align*}


# Spc commands


## Spacemacs config

spc fed  - edit spacemacs dotfile
spc feR  - reload spacemacs config


## toogle

spc tn    - toogle line number


## UI toogles

spc TF    - toogle fullscreen mode


## file

spc ft    - toogle neotree
spc ff    - open file


## project

Create en empty file named .projectile in your project root directory

spc pp    - switch project
spc pf    - find a file in your project
spc /     - find text in project


## buffer

spc tab   - last buffer 
spc bn    - next buffer
spc bb    - show the list of current buffers
spc bd    - delete buffer


## window

spc wS    - split windows vertical
spc nb of window - switch to <number of window>
spc wc    - close a window


## git

spc gs    - git statu


## shell

spc '     - toogle the little shell


## others

spc h[x]  - help on [x]
spc zX    - increase decrease font size


## : commands

:shell    - start a shell in a buffer


# Packages

spc spc package-install to install a package

