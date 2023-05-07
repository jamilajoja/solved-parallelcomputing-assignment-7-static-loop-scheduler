Download Link: https://assignmentchef.com/product/solved-parallelcomputing-assignment-7-static-loop-scheduler
<br>
Static Loop Scheduler

As usual all time measurements are to perform on the cluster.

<h1>1           Preliminary</h1>

<strong>Question: </strong>Before anything, we will need to get timing for sequential execution. Navigate to the sequential/ directory. Compile the sequential code with make sequential and get sequential time by running make bench on mamba.

<strong>Question: </strong>Rewrite the numerical integration problem using the looping construct. There is a sequential implementation of the looping construct in sequential/ directory. The construct is in seq loop.hpp while the test codes for the looping constructs are in loopsample.cpp. Write that code in static/static sched.cpp. Write the code so that it outputs the integral value on stdout and the time it takes to make the computation on stderr.

You can test the correctness of your sequential implementation using the looping construct with make test from the static/ directory.

The program should take the following command line parameters:

<ul>

 <li>functionid, same as in numerical integration assignment</li>

 <li>a, same as in numerical integration assignment</li>

 <li>b, same as in numerical integration assignment</li>

 <li>n, same as in numerical integration assignment</li>

 <li>intensity, same as in numerical integration assignment</li>

 <li>nbthreads, an integer indicating the number of threads that should perform the numerical integration Ignore nbthreads for your sequential adaptation.</li>

</ul>

<h1>2           Writing a static loop scheduler</h1>

Loop schedulers are used essentially whenever the code reads like your stereotypical <em>for </em>loop. In the previous assignment, transform would be a stereotypical for loop, but reduce could also be written this way. Here we will use the numerical integration example.

A static loop scheduler is the simplest way to achieve some parallelism. We will use it to make the numerical integration problem parallel.

Essentially, with <em>T </em>threads, each thread will do exactly  of the loop iterations. So that if the loop has 100 iterations and there are four threads, the first threads will execute loop iterations from 0 to 24, the second will execute iterations from 25 to 49, …

Be careful of what happens when the number of threads is not a diviser of the number of iterations. <strong>Question: </strong>Rewrite the looping construct to execute in parallel using a static scheduler. You can still use make test to test your code.

1

You will need to implement the parfor function to create threads, execute the before function, distribute the loop iterations to the different threads using a static distribution and execute them, and finally execute the after function.

You may also need to add functions to the looping construct abstraction to enable controlling the number of threads and add a call to that function from your main code. (Pass the value from the nbthreads command line parameter.)

<strong>Question: </strong>Report time and speedup across a range of precision and intensity. Your code MUST pass the test before you can use make bench to start the PBS jobs. Once they are complete, plot the charts with make plot. Note: you must run these commands from within the static/ directory. <strong>Question: </strong>Does the speedup you achieve look right?