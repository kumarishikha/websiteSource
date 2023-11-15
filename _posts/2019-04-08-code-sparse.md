---
layout: post
title:  "Coding Sparse Matrices"
date:   2019-03-16
---

<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>


**Creating CSR format from Dense format :**

A : dense matrix 
V : non zero values of A
J : column numbers
I : indices in J where new rows starts
isSymm : if A is symmetric, we need not store all non zero values. We can only store "half" of those .


```cpp

#include <bits/stdc++.h>
using namespace std;

void createCSR(vector<std::vector<double> >& A, int rows , int cols , int isSymm,vector<double>& V,vector<int>& I , vector<int>& J)
{	
	if (isSymm ==0)
	{
                //currI stores the value which will be put in the I array   
		int currI =0 ;
		for (int i = 0; i < rows; ++i)
		{I.push_back(currI);
			for (int j = 0; j < cols; ++j)
			{ double val = A[i][j];
				
				if (val!=0)
				{
					V.push_back(val);
				
					J.push_back(j);
				}
			}
			currI=J.size();
		}
I.push_back(J.size());

	} 

	else {
		int currI =0 ;
		for (int i = 0; i < rows; ++i)
		{I.push_back(currI);
//if A is symmetric, j need not iterate over all columns. 
//We only iterate over the lower triangular half of the matrix
			for (int j = 0; j <= i; ++j)
			{ double val = Vm[i][j];
				if (val!=0)
				{
					V.push_back(val);
					J.push_back(j);
				}
			}
			currI=J.size();
		}
I.push_back(I.size());
	}

}

```

**Matrix Vector Product when matrix is in CSR format**

```cpp
// considering A is in CSR format , implement matrix vector product Ax = result

#pragma once
#include <bits/stdc++.h>
using namespace std;

vector<double>  matrix_vector_product(vector<double>& V , vector<int>& I , 
vector<int>& J , vector<double>& x , int isSymm, vector<double>& result)
{	int n = IA.size()-1;


	if (isSymm ==0)
	{
		for (int i = 0; i < n; ++i)
	{
		int i1 = IA[i];
		int i2 = IA[i+1] - 1;
		for (int j = i1; j <= i2; ++j)
		{
			result[i] += V[j]*x[JA[j]];
		}
	}
	}

	else {
		for (int i = 0; i < n; ++i)
	{
		int i1 = IA[i];
		int i2 = IA[i+1] - 1;
		for (int j = i1; j <= i2; ++j)
		{
			result[i] += V[j]*x[JA[j]];
			if (JA[j]!=i)
			{
				result[JA[j]] +=V[j]*x[i];
			}	

		}
	}

		
	}

	return result ;
}

```
