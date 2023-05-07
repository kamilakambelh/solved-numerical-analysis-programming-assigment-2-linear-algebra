Download Link: https://assignmentchef.com/product/solved-numerical-analysis-programming-assigment-2-linear-algebra
<br>






Instructions for submission:

<ul>

 <li>Please submit a PDF file that includes all answers and ALL THE CODE you used (even inquestions that do not require to hand in an *.py file – your code should be in the PDF). The code in the PDF file must be IDENTICAL to the code in the *.py files you submit (below in (b)). This PDF file should be readable so that you could get constructive remarks. Make sure you edit your code so that it looks nice, and in particular, DO NOT USE Print Screens! The code should appear in the PDF file as text. You should submit a printed copy to the checkers box and and also a digital copy as instructed below in (b).</li>

 <li>In addition you should submit four *.py files (py; myeig.py; myGD.py; and Krank.py), and one *.npy file (’cities coor.npy’).</li>

 <li>Compress the PDF file of (a) and the files py, myeig.py, myGD.py, Krank.py and ’cities coor.npy’ of (b), into a SINGLE *.zip (you can also use *.rar, but no other format!) named YourID.zip (for example: 201920209.zip) and upload the file through the ”matalot lehagasha” section in the moodle page of the course. Make sure that the file names, function signatures and input and output data structures are EXACTLY as the ones specified in the questions below. Files with names or signatures which are different in any way from what is instructed WILL NOT BE CHECKED.</li>

 <li>The functions mylu, myeig, myGD and Krank must NOT print to the terminal, display plots or images, read or write to files or in general, do anything except for executing the algorithm for which they are intended to according to the instructions in the questions below.</li>

 <li>If you call functions from imported Python libraries (e.g numpy and etc.) all import statements MUST be included in the *.py file. For example, if you used a function from numpy in the implementation of myeig, you must include the import statement inside py.</li>

</ul>

Some general (and hopefully helpful) advice:

<ul>

 <li>There’s no need to check the validity of the input inside the functions, this is not a programming course. For instance, the function py below requires a symmetric matrix A, there’s no need to check if the inputed A is indeed symmetric.</li>

 <li>You may and are encouraged to use built-in library functions of Python whenever possible,except for (obviously) implementations of Python for an algorithm which you are required to implement in this exercise. For example, you can and should use some Python implementation to sort the eigenvalues in question 2 and not write your own Sort function (but obviously <strong>cannot </strong>use Python’s LU decomposition).</li>

 <li>For students who are having trouble with coding, take a look athttps://docs.scipy.org/doc/numpy/user/quickstart.html. It includes a nice quick tutorial for Python’s numpy library which should have most of what you need for this course.</li>

</ul>

<ol>

 <li>Implement LU factorization.</li>

</ol>

Your function should have the signature mylu(A,pivot), and return a Python list [L,U,P,Q] where

A            Matrix to factorize

pivot 0 – no pivoting, 1 – partial pivoting, 2 – complete pivoting.

L,U           <em>L </em>and <em>U </em>as defined by the LU algorithm.

P          Permutation matrix as defined for partial and complete pivoting. Q      Permutation matrix as defined for complete pivoting.

The algorithm should satisfy

<table width="171">

 <tbody>

  <tr>

   <td width="101">pivot = 0</td>

   <td width="70"><em>A        </em>=<em>LU</em></td>

  </tr>

  <tr>

   <td width="101">pivot = 1</td>

   <td width="70"><em>PA </em>=<em>LU</em></td>

  </tr>

  <tr>

   <td width="101">pivot = 2</td>

   <td width="70"><em>PAQ</em>=<em>LU</em></td>

  </tr>

 </tbody>

</table>

<strong>Important</strong>: The argument and output matrices A,L,U,P and Q <strong>must </strong>all be numpy arrays, that is, of type ndarray.

(See https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html)

<ol start="2">

 <li>Implement Jacobi’s iterations to find the eigenvalues and eigenvectors of a symmetric matrix.</li>

</ol>

Your function should have the signature myeig(A), and return a Python list [D,V] where

A Matrix to diagonalize.

D Diagonal matrix with SORTED eigenvalues (largest to smallest) on the diagonal. V Matrix of eigenvectors.

The matrices <em>V </em>and <em>D </em>should satisfy <em>V DV <sup>T </sup></em>= <em>A</em>. You may assume that the entries of <em>A </em>are real (i.e., <em>a<sub>i,j </sub></em>∈ R).

<strong>Important</strong>: The argument and output matrices A,D and V <strong>must </strong>all be numpy arrays, that is, of type ndarray.

(See https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html)

<ol start="3">

 <li>Download the file npy from the moodle site and use the load function of numpy to load the file into an ndarray variable named ’dists’. The file contains the pairwise distances between 312 cities, specifically, dists is a matrix of size 312 × 312, with</li>

</ol>

dists(<em>i,j</em>) = k<em>x<sub>i </sub></em>− <em>x<sub>j</sub></em>k

where <em>x<sub>i</sub>,x<sub>j </sub></em>∈ R<sup>2 </sup>are the coordinates in the plane of cities <em>i </em>and <em>j </em>respectively, and k·k is the Euclidean norm.

<ul>

 <li>Let <em>X </em>∈ R<sup>312×2 </sup>be a matrix whose <em>i</em>th row is <em>x<sub>i</sub></em>. Find an expression for <em>XX<sup>T </sup></em>in terms of the matrix dists.</li>

 <li>The coordinates <em>x</em><sub>1</sub><em>,…,x</em><sub>312 </sub>cannot be recovered uniquely from <em>XX<sup>T </sup></em>. Explain why.</li>

 <li>The coordinates of the first 5 cities are</li>

</ul>

Find <em>x</em><sub>1</sub><em>,…,x</em><sub>312</sub>, and write them as a 312 × 2 ndarray into a .npy file named ’cities coor.npy’, using the save function of numpy. In addition, write the coordinates of the first 10 cities to the PDF file.

<ol start="4">

 <li>Implement Gradient Descent iterations <em>~x<sub>k</sub></em><sub>+1 </sub>= <em>~x<sub>k </sub></em>− <em>a </em> ∇<em>f</em>(<em>~x<sub>k</sub></em>) for a general function <em>f</em>(<em>x</em>) : R<em><sup>n </sup></em>→ R. Your function should have the signature myGD(f,gradf,x0,a,tol,maxiter), and return a Python list [y, iter] where</li>

</ol>

gradf    Function handle to ∇<em>f</em>(<em>x</em>) x0  Initial vector to start the iterations from

<ul>

 <li>Step size</li>

</ul>

tol             Tolerance

maxiter Maximal number of iterations

y           Final approximation of the vector that minimizes f iter    Number of iterations until convergence

where the tolerance tol is an upper bound on k<em>x<sub>i</sub></em><sub>+1</sub>−<em>x<sub>i</sub></em>k to be used as the stopping criteria. Use myGD to minimize the Rosenbrock function <em>f</em>(<em>x,y</em>) = (1 − <em>x</em>)<sup>2 </sup>+ 100(<em>y </em>− <em>x</em><sup>2</sup>)<sup>2 </sup>with tol = 10<sup>−6</sup>, the parameter <em>a </em>= 0<em>.</em>001 and the starting point <em>x</em><sub>0 </sub>= (2<em>,</em>2). How many iterations did you need in order to achieve the approximation?

<ol start="5">

 <li>In this question we would like to compress an image using the SVD decomposition.

  <ul>

   <li>Download the file png from the moodle site.</li>

   <li>Read the image into an ndarray variable in Python named ’bwmandril’ using the imread function of matplotlib</li>

   <li>Display the image using the imshow function of matplotlib library, with the flag cmap=’gray’ (you should see a gray-scale image of a mandrill monkey displayed on the screen now).</li>

  </ul></li>

</ol>

Answer the following questions:

<ul>

 <li>Plot the singular values of the decomposition and decide according to their graph howmany singular values are needed.</li>

 <li>Create a function which gives a rank-<em>k </em>approximation of the image. Your function should have the signature Krank(A,k), and return a Python list [Uk, Sk, Vk] where</li>

</ul>

A A matrix of size <em>m </em>× <em>n </em>k The rank of the approximation

Uk <em>m </em>× <em>k </em>matrix

Sk <em>k </em>× <em>k </em>matrix of the singular values

Vk <em>n </em>× <em>k </em>matrix

The rank-<em>k </em>approximation of A should be <em>A<sub>k </sub></em>= <em>U<sub>k </sub></em>· <em>S<sub>k </sub></em>· <em>V<sub>k</sub><sup>T</sup></em>

<strong>Important</strong>: The argument and output matrices A,Uk,Sk and Vk <strong>must </strong>all be numpy arrays, that is, of type ndarray.

(See https://docs.scipy.org/doc/numpy/reference/generated/numpy.array.html)

<ul>

 <li>Use the Krank function to reconstruct an approximation of the image using just <em>k </em>singular values (the number <em>k </em>is for you to decide upon). Add your approximated image to the PDF file (use the matplotlib command imsave, NO Print Screens).</li>

</ul>


