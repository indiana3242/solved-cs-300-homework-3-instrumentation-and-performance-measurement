Download Link: https://assignmentchef.com/product/solved-cs-300-homework-3-instrumentation-and-performance-measurement
<br>
The intention of this homework is to make you understand program instrumentation and performance measurement and compare your real results with analytical complexity.  You will also understand the details of hash tables.

In this homework, you will measure and analyze the performance of hash-tables with linear probing. You will perform the following:

<ol>

 <li>You will create a hash table of integers employing linear probing of the appropriate size (call this M)</li>

 <li>You will randomly generate hash-table transactions (that is, inserts, deletes and finds).<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> You can assume that inserts, deletes and finds occur in proportion <em>i:d:f</em> where <em>i+d+f=8</em> and none of <em>i, d</em>, or <em>f</em> equal to 0, and <em>i &gt; d </em>(so the load factor monotonically grows)  and <em> d,f  ≥ 1</em>. So, you can decide (randomly) on the type of a transaction by generating a random integer <em>t</em>, and then computing <em>m =</em> <em>t</em> mod <em>8</em>. If <em>m</em> is between 0 and <em>i – 1</em>, then decide on an insert transaction, if <em>m</em> is between <em>i</em> and <em>i+d–1, </em>then decide on a delete transaction, otherwise decide on a find transaction. Assuming the random number generator is giving out truly random numbers, this procedure should approximate the desired transaction probabilities satisfactorily when you have a large number of transactions.</li>

</ol>

There are 8 possible combinations of the parameters satisfying the requirements, but we suggest that you experiment with only 3 of them :

<table width="0">

 <tbody>

  <tr>

   <td width="22"><em>i </em></td>

   <td width="22"><em>d </em></td>

   <td width="22"><em>f </em></td>

  </tr>

  <tr>

   <td width="22">6</td>

   <td width="22">1</td>

   <td width="22">1</td>

  </tr>

  <tr>

   <td width="22">4</td>

   <td width="22">2</td>

   <td width="22">2</td>

  </tr>

  <tr>

   <td width="22">2</td>

   <td width="22">1</td>

   <td width="22">5</td>

  </tr>

 </tbody>

</table>




<ol start="3">

 <li>Before each transaction you will note

  <ul>

   <li>the type of the transaction,</li>

   <li>the current load factor of the hash table (l= N / M where N is the number of entries currently in the hash table)</li>

  </ul></li>

</ol>

and after the transaction is complete you will note  • whether the transaction succeeded or failed

<ul>

 <li>how many probes were conducted.</li>

</ul>

Since for a given table size M you will be counting the transactions, you need not store the information for each transaction, but you can keep 6 tables of M+1 entries (one for each combination of the type of transaction and outcome). Each table entry will contain the <strong>total number of transactions</strong> and the <strong>total number of probes</strong> of that type and outcome conducted.  For example, when operating with M=10000 (you really should use a prime M!), the first table may hold the data for successful inserts (where you were able actually insert the data – as opposed to a failed insert where the data to be inserted was actually in the table or the table was full.) An entry in this table, say entry 6000, can hold the total number of such transactions and the total number of probes for those transactions where there were exactly 6000 entries in the hash table just before the successful insert.  After all these transactions are completed, you can compute for each the load factor, (e.g., 6000/10000), the average number of probes for each specific transaction and outcome type.




<ol start="4">

 <li>You can generate the integers to be used for each transaction again using the random number generator. It would better to limit the range of the integers to 10M so that most integers have a decent chance of being deleted or searched. You can generate such integers by generating a</li>

</ol>

random number and taking mod 10M.

<ol start="5">

 <li>You should generate transactions until the either the table becomes full or you have a total of 1,000,000 transactions.</li>

 <li>You should output your statistical data in a format (say comma or tab separated format) that can be imported into Microsoft Excel or Open Office Spreadsheet. You should figure out how to do this.</li>

 <li>Once you have all the data, you should then use Microsoft Excel or Open Office Spreadsheet so that you can generate nice plots of l versus average number of probes for each of the transaction and outcome combinations. You should prepare a total of 6 plots each showing three curves for the three parameter (i.e., <em>i</em>, <em>d</em>, <em>f</em>) combinations above. For example, the first graph may be titled “The average number of probes for successful insert operations versus load factor”.</li>

 <li>You should <strong>either</strong> use a hash function like <em>x </em>mod <em>M </em>that we used in class <strong>or</strong> another hash function of your choice that is suitable for <strong>linear</strong> <strong>probing</strong> (like extracting some bits from the middle of the integer (using bit operations) and then treating these bits as an unsigned integer and then computing that integer modulo <em>M</em>. You can do research on the web or in other books in the library for interesting integer hash function to use.</li>

 <li>You should use the <strong>hash-table implementation with linear probing</strong> given in the text book. However, you will need to modify this implementation, so that the resizing operation is removed (just for the sake of this homework, though!). Another important change will be to change the findpos(x) method so that it handles deleted items properly; the code in the course slides assumes that deleted items are skipped over when inserting new items.<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a> This implies an insert is implemented by actually a find followed by an insert if find fails. You should also add new private data items and possibly new private methods so that you can keep the statistics properly, and modify the implementation of the methods (such as insert, delete and find) so that the number of probes are counted properly and recorded.</li>

</ol>

At the end of the homework, you should submit the following:

<ol>

 <li>A short report (as a word or pdf document)

  <ul>

   <li>Describing the changes you made to the hash table code to implement linear probing and keeping statistics and the hash function you chose to use.</li>

  </ul></li>

</ol>

<ul>

 <li>Showing the graphics you obtained from the statistics you collected in your runs. Please make sure that your plots are accurate and readable with the curves and axes appropriately labeled.</li>

 <li>Ending with any conclusions you can draw from your results.</li>

</ul>




<ol start="2">

 <li>Your source code files.</li>

</ol>

Your homework should be submitted to SUCourse at the deadline given on the first page. We suggest that you take our warning above that indicates that you should submit only your work and not collaborate with others. <strong>We assume that by submitting your homework in the manner below, you are certifying that you are submitting your own work.</strong>

You should follow the following steps:




<ul>

 <li>Name the folder containing your source files as <em>XXXXX-NameLastname </em>where <em>XXXXX</em> is your student number. Make sure you do NOT use any Turkish characters in the folder name. You should remove any folders containing executables (Debug or Release), since they take up too much space.  <strong>You should also put your report file labeled as <em>doc </em>or<em> XXXXX-NameLastname.pdf</em> in this directory.</strong></li>

 <li>Use the Winzip program to compress your folder to a compressed file named <em>XXXX- NameLastname.zip</em>. After you compress, please make sure it uncompresses properly and the uncompress produces the original folder exactly.</li>

 <li>Submit this compressed file in accordance with the deadlines above.</li>

</ul>




If the file you submitted is not labeled properly as above, if it does not uncompress, if the source code(s) do(es) not compile and if we can not open and print your report file, we regretfully will have to give you 0 credits for the homework. So please make sure all these steps work properly.

<a href="#_ftnref1" name="_ftn1">[1]</a> You should use the <strong>rand( )</strong> function available in C++ to generate random integers. If you initialize the random number seed (using <strong>srand(seed), e.g., srand(4)</strong>) to the same number, you will always get the same random sequence of random numbers. This is actually what you want, since you want the same sequence every time you run the program as you are developing it so that it would be easier to debug.




<a href="#_ftnref2" name="_ftn2">[2]</a> You may actually want to get rid of findpos() altogether and embed it into the relevant other methods.