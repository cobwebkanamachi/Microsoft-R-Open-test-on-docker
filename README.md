# Microsoft-R-Open-test-on-docker
I saw Microsoft R Open, so testify it with docker.
<BR>
R runs with messages shown bellow after installation.
<PRE>
Microsoft R Open 3.2.3
Default CRAN mirror snapshot taken on 2016-01-01
The enhanced R distribution from Microsoft
Visit http://go.microsoft.com/fwlink/?LinkID=722555 for information
about additional features.

Multithreaded BLAS/LAPACK libraries detected. Using 8 cores for math algorithms.
</pre>
1. Installation procedures<BR>
I follow this article. See it.<BR>
https://github.com/nuest/docker-mro/issues/4 <BR>
<BR>
2. Execution Demo.R<BR>
benchmark executed shown bellow(MRO with MKL).
<pre>
> source("demo.R")
   R Benchmark 2.5
   ===============
Number of times each test is run__________________________:  3

   I. Matrix calculation
   ---------------------
Creation, transp., deformation of a 2500x2500 matrix (sec):  1.14 
2400x2400 normal distributed random matrix ^1000____ (sec):  0.664 
Sorting of 7,000,000 random values__________________ (sec):  0.763 
2800x2800 cross-product matrix (b = a' * a)_________ (sec):  0.456 
Linear regr. over a 3000x3000 matrix (c = a \ b')___ (sec):  0.327000000000001 
                      --------------------------------------------
                 Trimmed geom. mean (2 extremes eliminated):  0.613600662712112 

   II. Matrix functions
   --------------------
FFT over 2,400,000 random values____________________ (sec):  0.575333333333332 
Eigenvalues of a 640x640 random matrix______________ (sec):  0.642333333333333 
Determinant of a 2500x2500 random matrix____________ (sec):  0.279666666666666 
Cholesky decomposition of a 3000x3000 matrix________ (sec):  0.246666666666665 
Inverse of a 1600x1600 random matrix________________ (sec):  0.271333333333336 
                      --------------------------------------------
                Trimmed geom. mean (2 extremes eliminated):  0.352117652345226 

   III. Programmation
   ------------------
3,500,000 Fibonacci numbers calculation (vector calc)(sec):  0.628666666666668 
Creation of a 3000x3000 Hilbert matrix (matrix calc) (sec):  0.378 
Grand common divisors of 400,000 pairs (recursion)__ (sec):  0.450999999999998 
Creation of a 500x500 Toeplitz matrix (loops)_______ (sec):  0.367333333333332 
Escoufier's method on a 45x45 matrix (mixed)________ (sec):  0.817 
                      --------------------------------------------
                Trimmed geom. mean (2 extremes eliminated):  0.47500289711991 


Total time for all 15 tests_________________________ (sec):  8.00733333333333 
Overall mean (sum of I, II and III trimmed means/3)_ (sec):  0.468191249034673 
                      --- End of test ---

Total test time: 49.173 seconds
</pre>
<BR>
3. Execution Demo.R on Native R<BR>
benchmark executed shown bellow(osx native R without MKL).
<pre>
   R Benchmark 2.5
   ===============
Number of times each test is run__________________________:  3

   I. Matrix calculation
   ---------------------
Creation, transp., deformation of a 2500x2500 matrix (sec):  0.983666666666667 
2400x2400 normal distributed random matrix ^1000____ (sec):  0.258333333333335 
Sorting of 7,000,000 random values__________________ (sec):  0.737 
2800x2800 cross-product matrix (b = a' * a)_________ (sec):  11.434 
Linear regr. over a 3000x3000 matrix (c = a \ b')___ (sec):  5.48 
                      --------------------------------------------
                 Trimmed geom. mean (2 extremes eliminated):  1.58379390400634 

   II. Matrix functions
   --------------------
FFT over 2,400,000 random values____________________ (sec):  0.405666666666671 
Eigenvalues of a 640x640 random matrix______________ (sec):  0.917666666666662 
Determinant of a 2500x2500 random matrix____________ (sec):  3.89633333333333 
Cholesky decomposition of a 3000x3000 matrix________ (sec):  4.56766666666667 
Inverse of a 1600x1600 random matrix________________ (sec):  3.37 
                      --------------------------------------------
                Trimmed geom. mean (2 extremes eliminated):  2.29257553634449 

   III. Programmation
   ------------------
3,500,000 Fibonacci numbers calculation (vector calc)(sec):  0.323000000000008 
Creation of a 3000x3000 Hilbert matrix (matrix calc) (sec):  0.285666666666666 
Grand common divisors of 400,000 pairs (recursion)__ (sec):  0.927666666666672 
Creation of a 500x500 Toeplitz matrix (loops)_______ (sec):  0.360333333333339 
Escoufier's method on a 45x45 matrix (mixed)________ (sec):  0.405000000000001 
                      --------------------------------------------
                Trimmed geom. mean (2 extremes eliminated):  0.36123292544307 


Total time for all 15 tests_________________________ (sec):  34.352 
Overall mean (sum of I, II and III trimmed means/3)_ (sec):  1.09463639338888 
                      --- End of test ---
</pre>
