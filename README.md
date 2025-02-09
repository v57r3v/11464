java c
Tutorial and Laboratories 
11464 - 11524G AR/VR for Data Analysis and Communication 
Basics of Data Visualisation - Week 1
Introduction 
In this tutorial will continue   practising   basic operations   in   R.   In   particular, you will   learn   about visualising data   in   R;   how to create   plots,   choosing a   plot   type   and   basics   of   data   visualisation.   This   is   a   basic   introduction to some of the   basic   plotting commands. 
It   is assumed that you are   now familiar with different   data   types,   how   to   subset   data   from   vectors   and data frames, and   how to enter   data or   read   data   files   which   was   covered   in   our   previous tutorial.   It   is   recommended to complete the tutorial from week 3   before attempting   this   tutorial.
Skills Covered   in this tutorial   include:
•            Plotting   in   Rstudio
• Basics of data visualisation
•            Using different   plot typesNote: Do   not copy-paste the commands. As you type   each   line, you   will   make   mistakes   and   correct   them, which   make you think as you go along.   Remember, that the   objective   is   that   you   understand   the commands and   master the concepts, so   you   can   reproduce   their   principles   on   your   own   later.
1. Plotting in RStudio 
One of the   most   powerful features of   R   is   its capability to   produce   a   different   range/style   of graphics   to visualise data quickly and easily.   When   a   plot   is   generated   in   Rstudio,   the   plots   are   displayed   in the   built-in   plotting window   in the   bottom-right   pane   (please   refer to the tutorial   in Week 2). This   window   has different options,   and   it   is   presented   in   Figure   1. 


Figure 1. The   plotting window   in   RStudio.   1)   Navigate through all the   plotting   history. 2) The   plot   is   displayed   in a   larger window. 3) The   image   is exported   as   image   of   FPF format.   4)   remove the current   plot from the   plotting   history. 5) clear all   plotting   history.
In this tutorial, we will   use two different datasets   (w1   and tree),   which   can   be   found   in   Canvas   in   the   Week 4   module. You can   read the data   as   follows:
#   read   data
w1 <- read.csv(file="w1.dat",sep=",",head=TRUE)
tree <- read.csv(file="trees91.csv",sep=",",head=TRUE)
Remember to   select your working directory, so the data   can   be   found
2. Using different types of plot functions 
2.1. Bar Plots A   bar   plot   is a graph that   represents categorical data   with   bars   of   different   lengths   proportional to   the values that they   represent. One axis of the   plot   shows   the   specific   categories   being   compared      and the other axis   represents   a   measured value.
Exercise 1. Create   a   bar   plot   of the tree data frame   using the   variable tree$C. This variable represents the class of trees for each tree   in the   dataset, thus,   simply   doing barplot(tree$C) will   not         give   us the   plot correctly. We   need to find the   number of trees   in   each   class   category. This   count   can   be quickly found   using the table()   function,   please complete the following   example.
# create   a   bar   plot
counts <- table(tree$C)
barplot(counts)
#   Edit the title of the   plot and   the   label   of the   axes
barplot(counts,
main="Total   Number of trees   in each class",
xlab="CLass of tree",
ylab="Trees")
You should always   annotate   your   graphs.   It   is a good   practice   as   a data analyst/scientist

You can also create a group   bar   plot,   where   you   can   compare   different variables.   One   way   to   achieve   this   is   using a stacked   bar   plot,   let’s do the   following.
# Generate   some   data
set.seed(112)
data <- matrix(sample(1:30,15) , nrow=3)
colnames(data) <- c("A","B","C","D","E")
rownames(data) <- c("var1","var2","var3")
#   plot a   stacked   bar   plot
barplot(data,
legend=rownames(data),
xlab="group")
Try to add   some   colour:      col=colors()[c(23,89,12)]
You can also create a grouped   bar   plot   using the beside=TRUE   parameter.   Please   do   the   following:
#   plot a   stacked   barplot
barplot(data,
legend=rownames(data),
xlab="group",
beside   = TRUE)
2.2. Histograms 
A   histogram   is a graphical   representation of the frequencies   (how   many times data   occurs)   that   data   appears within certain   ranges.   It   is similar to   a   bar chart,   in a   histogram   the   height   of   each   bar represent   how   may fall   into   each   range, you can select what   ranges to   use.
Exercise 2. Create   a   histogram of the w1 data frame   using the variable vals.   We   can   do   this   using the hist() function,   please complete the following example.
# create   a   histogram
hist(w1$vals)
#   Edit the title of the   plot and the   label   of   x   the   axis
hist(w1$vals,main="Distribution of vals variable",xlab="vals")

As you can see, the   intervals were   automatically obtained   by   R.   However,   if you   need/want to change the   number of   intervals, we can specify the   number   of   breaks   using the breaks parameter.
Remember   If you would   like to   know   more about the other options   checkout the   help   page   by   using help(hist). Try the following   instructions and observe the   results.
# change the   number of   breaks   and
hist(w1$vals,breaks=2)
hist(w1$vals,breaks=4)
hist(w1$vals,breaks=6)
hist(w1$vals,breaks=8)
hist(w1$vals,breaks=12)
However, the   breaks are   not always   maintained according to the   integer   passed to   the breaks parameter. The   reason for that   (as   per the documentation)   is that   if you give the breaks parameter   a   single   number,   it   is treated as a suggestion as   R   will   use   its   own   breakpoints to   create   a   pretty-looking   plot.   If you want to force   it to   be a specific   number of   breaks,   you   can   do   the   following.
# generate some   random   data
x <- rnorm(296)
# create the   histogram
hist(x,   breaks=c(-4,-3,-2,-1,0,1,2,3,4,5))
# another way   using the vals   variable
hist(w1$vals,   breaks = seq(min(w1$vals),   max(w1$vals),   length.out = 7))
2.3. Boxplots 
A   boxplot   is a graphical   representation of the   median, quartiles,   maximum,   minimum of   a   data   set, and therefore the overall distribution of your data.   Another   great   use   of   boxplots   is   that   it   can tell you about the outliers and what their values   are.   It   can   also   give you   information   if the   data   is symmetrical,   if your data   is skewed, or   how tightly your data   is   grouped.   Let’sa   look   how   we   create   a   boxplot. 
Exercise 3. Create   a   boxplot of the w1 data frame   using   the   variable vals.   We   can   do   this   using   the boxplot() function,   please complete the following example.
# create   a   boxplot
boxplot(w1$vals)
#   Edit the title of the   plot and the   label   of   x   the   axis
boxplot(w1$vals,main='Leaf   BioMass   in   High CO2   Environment',ylab='BioMass of   Leaves')

If you want to   know   more   about   boxplots   have a   look   at this   link: 
https://towardsdatascience.com/under standing-boxplots-5e2df7bcbd51 
You can change the orientation of the   plot,   from   vertical   (as   figure   above) to   a   horizontal   boxplot. This can   be changed   using the horizontal = TRUE parameter. Again,   for   more   information   about   this   function, you can   use the help(boxplot) command. Complete   the following   and   observe   the   results.
# create   a   boxplot
boxplot(w1$vals,
main='Leaf   BioMass   in   High CO2   Environment',
xlab='BioMass of   Leaves',
horizontal=TRUE)
So   now,   let’s   use the tree   data set   and create a   boxplot   with   different   levels   in the   same   plot.   In this example, the data   is   held   in tree$STBM and the different   levels   arestored   in tree$C.   Use the   following command and observe the   results. 
# creat代 写11464 – 11524G AR/VR for Data Analysis and Communication Basics of Data Visualisation - Week 1Python
代做程序编程语言e   a   boxplot
boxplot(tree$STBM~tree$C,
main='Stem   BioMass   in   Different CO2   Environments',
ylab='BioMass of Stems')
Note that you will see four outliers which   are   presented   as   little circles.   Also,   the   thick   line   in   the middle of each   boxplot   is the median of each   level.   If we   order   all the   data   points   for   each   level   and select the   data   point   in the   middle, that   is the   median.   For example,   if we   have the following ordered   list   (1,2,5,6,11), the   median   is   5.
2.4. Scatter Plots 
A scatter   plot   provides a graphical view of the   relationship   between two   sets   of   numbers.   In   a   scatter   plot, each data   point   is   plotted as a   point whosex   andy   coordinates   describe   its values   for   the   two variables. The plot() function   allows   to   plot   pairs   of   data   points   as   an   x-coordinate   anday-   coordinate.   Let’s   have a   look   how we create a   scatter   plot. 
Exercise 4. Create   a scatter   plot of the w1 data frame   using the   variable vals.   We   can   do   this   using   the plot() function,   please complete the   following example.
# create   a   scatter   plot
plot(tree$STBM,tree$LFBM)
#   Edit the title of the   plot and the   label   of   x   the   axis
plot(tree$STBM,tree$LFBM,
main="Relationship   Between   Stem and   Leaf   Biomass",
xlab="Stem   Biomass",
ylab="Leaf   Biomass")  

An   interesting feature of scatter   plots   is that they   help   us to   identify   any   relationship   between the   variables.   In the   previous   plot,   it   is very clear that there   is a   positive association   between   the biomass   in the stems of the tree and the   leaves   of the tree. We   can   compute   the   correlation between these two variables to   know the strength of this   relationship.   Please   do the   following.
# find the   correlation
cor(tree$STBM,tree$LFBM)
[1] 0.9115949
If you want to   know   more about   correlation   have a   look   at   this   link:
https://www.mathsisfun.com/data/correlation.html
We can see that there   is a strong   positive   correlation   between the   two variables.   Now,   let’screate   a   plot that   includes this   information, we   need to   add a   line of   best   fit   or   regression   line.   Remember,   linear   regression   is a   method to   model the   relationship   between two variables, the   result   is a   linear      regression equation that can   be   used to   make   predictions about the   data.   We   will   not   cover this technique further in this   unit.
plot(tree$STBM,tree$LFBM,
main="Relationship   Between Stem and   Leaf   Biomass",
xlab="Stem   Biomass",
ylab="Leaf   Biomass")
# fit   aline   of   best   fit
abline(lm(tree$LFBM~tree$STBM), col="red")
2.5. Time Series Plots 
A time series   plot   is a   line chart that   allows   us to   study the   evolution   of   one   or   several   variables through time. Generally, a time series   is an   equally   spaced   sequence   of   data   points   ordered   in   time.      These   kinds of   plots are commonly   used to   monitor   industrial   processes, sensor   data   (e.g.,   weather),   or tracking corporate   business   metrics. The plot() function also allows to   plot   time   series   data.   Let’s         have   a   look   how we create   a   line   plot. 
Exercise 5. Create   a time series   plot of the tree data   frame   using the   variable   RTMGCC.   We   can   do   this   using the plot() function   by   passing the   parameter type=‘l’,   please complete the following example.
# create   a   line   plot
plot(tree$LFBM, type =   'l')
#   Edit the title of the   plot and the   label   of   both   axes
plot(tree$LFBM,
type   =   'l',
main='Leaf   BioMass   in   High CO2   Environment',
ylab='BioMass of   Leaves',
xlab='Samples')  

You can   plot   multiple   lines   in a single   plot, to   do that you   can   use   the points() function.   Please   complete the following.
#   multiple   lines
plot(tree$LFBM,
type   =   'l',
col   =   'blue',
main='Leaf   BioMass   in   High CO2   Environment',
ylab='BioMass of   Leaves',
xlab='Samples')
# then add the   rest of the   lines,   one   at   a   time
points(tree$STBM, type='l', col='red')
points(tree$RTBM, type='l', col='forestgreen')
Consider these options when   plotting a vector of observations.
X   <- 1:8
Y <- c(4,5.5,6.1,5.2,3.1,4,2.1,0)
par(mfrow=c(3,2))          # c(nrows,ncols)
plot(X,Y, type='p',   main="type='p'")
plot(X,Y, type='o',   main="type='o'")
plot(X,Y, type='b',   main="type='b'")
plot(X,Y, type='l',   main="type='l'")
plot(X,Y, type='h',   main="type='h'")
plot(X,Y, type='s',   main="type='s'")
To   reset the   plot style. you can   usedev.off(),   but   it clears also   all your   plots.   Also,   you   can   use   the   following,   par(mfrow = c(1,1)).
3. Take Home Exercises 
3.1 Titanic dataset. This dataset contains survival   status   of   passengers   on   the   Titanic.   The   dataset   is   a tab-separated file and saved as a   txt   file.   Information   included   in   the   dataset:   names,   passenger class, age, gender, and survival status.   More   information   about this   dataset   can   be   obtain   from:
http://www.statsci.org/data/general/titanic.html. Inspect the data set   and obtain the   following:
1.          Obtain the total count of   passengers who survived   and   didn’t   survived   for   each   passenger   class   in the dataset.   Hint: table() 
2.          Make a group   bar   plot with the   total   count   of those   who   survived   and   didn’t   survive   for   each   passenger class,   use the “red” and “green” colours to differentiate   those   who   survived   and            not   survived.
3.          Add a   legend   in the to   left of the   plot that   represents the survival   status.
4.          What   passenger class   had the worst death   toll?
5.          Make stacked   bar   plot with the count   of those   who   survived   and   didn’t   survive for   each   gender,   use the “red” and “green” colours to   differentiate those who   survived   and   not         survived.
6.          What gender   had   more   loses?
3.2 Pupae dataset. This dataset contains data from   experiment   where   larvae   were   left   to   feed   on   Eucalyptus   leaves   in a glasshouse with two different   levels of temperature   and   CO2.   For   more information   about   the   variables   of   this   dataset, goto:
https://rdrr.io/github/RemkoDuursma/lgrdata/man/pupae.html 
Inspect the data set   and obtain the   following:
1.          Convert ‘Co2_treatment’ variable to a factor. What   levels   did you   obtained?   Hint: as.factor(). 
2.          Make a scatter   plot of   Frass   vs   PupalWeight,   with   blue   solid   circles   for   a   CO2_treatment   of
280 and   red for 400. Also add a   legend.   Set   the   colours   of the   plot   to   correspond   with   the   level of CO2_treatment   (280 and 400).   Hint: help(pch) 
3.          Make a separated   plot side   by   side for   each   of the   two   temperature   treatments   (ambient   and elevated).   Example   below   in   Figure 3.1.
4.          In the above   plot,   make sure that   the   X   and   Y   axis   ranges   are   the   same   for   both   plots.   Hint:   xlimandylim.
5.          Instead of   making two   plots,   make a   single   plot that   uses   two   colours   to   differentiate   the   CO2_treatment   (280 and 400) and different symbols to   distinguish   the temperature treatments   (ambient and   elevated).   Example   below   in   Figure   3.2.
6.          Do you see any   difference   between the   treatments?

Figure 3.1. Plot side   by side for each of the   two   temperature   treatments   (ambient   and   elevated).

Figure 3.2. A single   plot that   uses two colours to   differentiate the   CO2_treatment   (280   and   400)   and   different symbols to distinguish the temperature treatments (ambient   and   elevated). 







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
