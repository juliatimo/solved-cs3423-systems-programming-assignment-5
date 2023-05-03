Download Link: https://assignmentchef.com/product/solved-cs3423-systems-programming-assignment-5
<br>
More Scripting – Python Edition

For this assignment, you will use <strong>Python 3 </strong>to create a simple templating engine. Your program should take as input a generic template with placeholders for generic data, a set of input files containing data which should be applied to the template, and a date. Instantiated templates using the input data will be output to a subdirectory.

This assignment requires <em>only </em>Python. <strong>Do not </strong>use the command line utilities used in the previous assignment. You are encouraged to explore the Python standard library (the <sub>shutil </sub>module may be particularly useful).

<h1>Data Format</h1>

Data will be stored in the same format as the data in Assignment 1. For each course with an enrollment greater than 50, your program will use the provided template to generate an advisory report specifically for them.

<ol>

 <li>Data files (i.e., of the same format as those generated in Assignment 1) will be stored inside a directory specified by the user.</li>

 <li>Each file within that directory will be named based on the department code (two or three uppercase alphabetic characters), a course number (exactly <strong>four </strong>digits), and ending with an extension of <strong><sub>.crs</sub></strong>.</li>

 <li>A course file consists of <em>exactly </em>five lines:

  <ul>

   <li><sub>dept_code </sub>(two or three character string) <sub>dept_name </sub>(string with possible whitespace)</li>

   <li><sub>course_name </sub>(string with possible whitespace)</li>

   <li>course_sched (string: either TH or MWF) course_start (start with no whitespace) course_end (string with no whitespace)</li>

   <li>credit_hours (integer)</li>

   <li><sub>num_students </sub>(integer representing number of enrolled students)</li>

  </ul></li>

 <li>Example file named <strong><sub>crs</sub></strong></li>

</ol>

MAT Mathematics Calculus I

TH 8/26/19 12/11/19

3

62




<h1>Templating</h1>

Templates will include variable names to be filled in with data using double square brackets. For any data file of the format described above, each of the variables (including the square brackets) should be substituted with the data’s actual value. Your program should work for <strong>arbitrary templates </strong>using the same variables listed below corresponding to the item values described. More than one variable may appear per line.

<ul>

 <li><strong>[[dept_code]]</strong></li>

 <li><strong>[[dept_name]]</strong></li>

 <li><strong>[[course_name]]</strong></li>

 <li><strong>[[course_start]]</strong></li>

 <li><strong>[[course_end]]</strong></li>

 <li><strong>[[credit_hours]]</strong></li>

 <li><strong>[[num_students]]</strong></li>

 <li><strong><sub>[[course_num]] </sub></strong>(the course number as specified in the filename of the .crs file)</li>

 <li><strong>[[date]] </strong>(see below)</li>

</ul>

<strong>Example Template:</strong><sup>*</sup>

<table width="605">

 <tbody>

  <tr>

   <td width="605">&lt;html&gt;&lt;body&gt;&lt;h1&gt;NOTICE OF OVERENROLLMENT – COURSE [[dept_code]] [[course_num]]<em>←-</em>–   [[date]]&lt;/h1&gt; &lt;p&gt;Dear Instructor,&lt;/p&gt;&lt;p&gt;Your course, [[course_name]], scheduled from [[course_start]] to<em>←-</em>[[course_end]], has exceeded normal capacity with an <em>←</em>enrollment of [[num_students]] students. This must be <em>←</em>corrected within thirty days or this issue will be referred <em>←</em>to the [[dept_name]] department for further review. &lt;/p&gt; &lt;p&gt;–   Administration&lt;/p&gt;&lt;/body&gt;&lt;/html&gt;</td>

  </tr>

 </tbody>

</table>

<sup>* </sup>This is <em>only a <strong>single </strong>example of a single template</em>! You must assume that multiple different templates, with various combinations of variables, will be ran against your program. Experiment with exercising your program using your own custom scripts, as none will be provided to you. This is to emphasize the notion that <em>no single template should be used as a test instrument; your script</em>

<em>will be tested against several unknown-to-you templates</em>.




<h1>Date Argument</h1>

The third command-line argument should be a date manually entered by the user of the format <strong>MM/DD/YYYY</strong>. This value should be substituted anywhere where <strong><sub>[[date]] </sub></strong>appears.

<h1>Output</h1>

All output files should be written to the directory defined by the last argument. This directory may or may not already exist. Each file should be named by the course’s department code and number, and with the extension <strong><sub>.warn</sub></strong>.

<h1>Script Execution</h1>

Your program should be invoked through a single bash file (see below) with <strong>four arguments: </strong>data directory, template file, date, and output directory. Assuming the program executes correctly, <u>no output should be printed to the screen</u>.

<strong>$ assign5.py ./data assign5.template 12/16/2021 ./output</strong>

<h1>Assignment Data</h1>

Sample input files can be found in:

<strong>/usr/local/courses/ssilvestro/cs3423/Fall19/assign5/data</strong>. <strong>Script Files</strong>

Your program should consist of exactly one file:

<ul>

 <li><strong><sub>assign5.py </sub></strong>– the main file which is initially invoked</li>

</ul>

<h1>Extra Credit (5 points)</h1>

Allow your program to take <em>optional </em>fifth and sixth arguments describing the character(s) surrounding the variables instead of double square brackets. This feature should work for the following characters as either the opening or closing symbol, “/”, “|”, “}”, and “{”. Note that these can be in any combination (e.g., starting with “<strong>{</strong>” and ending with “<strong>|</strong>”) If no fifth and sixth arguments are passed, the program should behave as normal. You may assume that if a fifth argument is passed, a sixth will be present, too.

<strong>Example:</strong>

<strong>$ assign5.py ./data assign5.template 12/16/2021 ./output </strong>’<strong>{</strong>’ ’<strong>|</strong>’

The above invocation should replace variables in the template such as <strong><sub>{date| </sub></strong>instead of <strong><sub>[[date]]</sub></strong>.

<u>Extra credit is not given to late assignments. </u>All requirements must be met to qualify for extra credit.


