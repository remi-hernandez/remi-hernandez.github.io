= Spacemacs
// See https://hubpress.gitbooks.io/hubpress-knowledgebase/content/ for information about the parameters.
:published_at: 2018-05-16
:hp-tags: spacemacs, tips, shortcuts
:hp-image: /images/spacemacs.png



#+TITLE: This is spacemacs title

#+OPTIONS: toc:nil

= Org 
== categories

   #+BEGIN_SRC c++
   void process_stuff(my_super_class* ptr)
   int a = 2;
   #+END_SRC

   #+BEGIN_SRC python
     def example(a, b):
        """
        in a src block use ctrlc ' (ctrlc + single quote) to edit the code block in editor
        use ctrlc ctrlc to evaluate it and made appear the results (but doesn't work for now)
        """
        print ("will process {} + {}".format(a, b))
        return (a,b)
     example(2, 18)
   #+END_SRC

== Commands
  | command        | action                                           |
  |----------------+--------------------------------------------------|
  | shift tab      | changes  fold                                    |
  | ctrlc and wait | all the commands with description will displayed |
  | ctrlc ctrle    | export file                                      |
  | ctrlc ctrlc    | compute part                                     |
  | ctrlc ctrlt    | cycle through TODO states                        |
  | ctrlc ctrld    | add a deadline to a TODO element                 |
  | ctrlc ctrls    | append a datetime                                |
 
== SPC commands
   spc mee    - export in different kind of files

== Todo & cie
*** TODO todo example
    DEADLINE: <2018-04-20 Fri>
    at the end of the title line (after example here) hit shift alt enter
    to go to the next line with another todo
    use ctrlc ctrld to add a deadline do a todo element
    
    1. under task one.
    2. [ ] under task two.
    3. [ ] 
    
*** DONE clycle through states
    CLOSED: [2018-05-15 Tue 13:16]
    use ctrlc ctrlt tou cylcle through states

*** use list [1/2]
    use ctrlc ctrlc on one line to set or unset the state
    - [ ] task one
    - [X] task two

*** use other list [50%]
    - [ ] item one
    - [X] item two

** Schedules
   SCHEDULED: <2018-05-15 Tue>
   use ctrlc ctrls to append a datetime
   move cursor on the datetime and use shift left / right to change the value
     
   

   


** commands (spc spc my_super_command)
   org-md-export-to-markdown     - export to a text file with markdown syntax (my_file.md)
  
** LaTex integration
  - Characters: \alpha \rightarrow \beta
  - $O(n \log n)$
  
  \begin{align*}
    3 * 2 + 1 &= 6 + 1\\
             &= 7
  \end{align*}

* Spc commands
** Spacemacs config
   spc fed  - edit spacemacs dotfile
   spc feR  - reload spacemacs config

** toogle
  spc tn    - toogle line number

** UI toogles
  spc TF    - toogle fullscreen mode
  
** file
   spc ft    - toogle neotree
   spc ff    - open file

** project
   Create en empty file named .projectile in your project root directory

   spc pp    - switch project
   spc pf    - find a file in your project
   spc /     - find text in project

** buffer
   spc tab   - last buffer 
   spc bn    - next buffer
   spc bb    - show the list of current buffers
   spc bd    - delete buffer

** window
   spc wS    - split windows vertical
   spc nb of window - switch to <number of window>
   spc wc    - close a window

** git
   spc gs    - git statu

** shell
   spc '     - toogle the little shell

** others
   spc h[x]  - help on [x]
   spc zX    - increase decrease font size

** : commands
   :shell    - start a shell in a buffer

* Packages
  
  spc spc package-install to install a package
  
  En tete a mettre en haut d'un fichier org pour les marges etc
  [org]
  ----
  #+LATEX_HEADER: \usepackage[margin=1in]{geometry}
  #+LATEX_HEADER: \usepackage[hidelinks]{hyperref}
  #+LATEX_HEADER: \usepackage{palatino}
  ----

    