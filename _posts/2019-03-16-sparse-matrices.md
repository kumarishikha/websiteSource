---
layout: post
title:  "Sparse Matrices - Storage Schemes"
date:   2019-03-16
---

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

**Simple definition** : A matrix which has “most” of its entries = 0 is a sparse matrix . For a formal definition of sparsity, we consider a ratio of zero valued entries and total number of entries .

**Example**

M =   $$ \begin{matrix} 1 & 0 & 0 & 1 \\  0 & 0 & 0 & 1 \\
 0 & 0 & 1 & 1 \\
  0 & 0 & 0 & 1  \end{matrix}$$

  Sparsity = $$\frac{10}{16} = 0.625$$

  When sparsity is greater than 0.5 , a matrix is called sparse .

  **Storage Schemes for Sparse Matrices**

  Usually, we store matrices in “dense” formats, wherein each entry (irrespective of whether it is 0 or non zero) is stored at a location. For the above matrix, there will be 16 units of integer memory allocated. But, since only 6 out of the 16 entries are non zero, can we come up with other ways of storing the matrix which requires lesses space?

**Coordinate Format(COO)**

In COO format, rather than storing all entries of a matrix, we instead store only the non zero values and their corresponding indices.

We work with 3 arrays :

I : to store the row number of non zero entry

J : to store the column number of non zero entry

V : to store the non zero value at index i,j

We can either go “row-wise” and save indices and values or we can go column wise. Following is an example of going row- wise (starting index is 0 as in C++ and not 1 as in MATLAB) : \\
I : 0, 0, 1, 2, 2, 3 \\
J : 0, 3, 3, 2, 3, 3 \\
V : 1, 4, 6, 8, 8, 6



BUT, what do we observe? We end up needing to store 18 number rather than 16 if we would have saved in dense format. So, when is it economical to use COO rather than dense format?

Let number of non-zero values be nz and number of zero values b z. For each non zero value, we store its coordinates and the value, meaning 3 units of space fr each non zero value.

If r and c are numbe rof rows and columns in the matrix, total number of entries in dense format = r*c . If 3nz < rc , then COO format saves us some space.

Noting ,\\
*z+nz = rc* :

*3(rc - z) < rc*

*z > 2/3(rc)*

Which means, if the number of zero values entries is greater than 2/3 times total number of entries, we end up saving space using COO format, rather than dense format.


**Compressed Sparse Row Format (CSR)**

Another format is CSR where the V and J arrays are the same as that for COO . The difference is for the "I" array. Rather than storing i coordinates for non zero values, we store the coordinate of the "J" array, where a new row starts.

For the above mentioned matrix M, we get the following arrays : \\
I : 0, 2, 3, 5, 6  \\
J : 0, 3, 3, 2, 3, 3  \\
V : 1, 1, 1, 1, 1, 1

Note : The last element of the I array will always contain value = number of rows+1 .

In general, if there are **m** number of non zero entries in a nxn matrix, COO format will require 3m space and CSR will require 2m + n+1 space .

**Compressed Sparse Column Format**

 It is the same as CSR format, except the values are read column wise. We save the row number of each non zero entry (in, say, array I), and the an array (say, J) would contain the indices in the array I where a new row starts .

I : 0, 2, 0, 1, 2, 3 \\
J : 0, 1, 1, 2, 6 \\
V : 1, 1, 1, 1, 1, 1
