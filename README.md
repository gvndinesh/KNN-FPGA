# KNN-FPGA
FPGA Implementation of iris Flower classification using KNN
This Project is done as a part of my VLSI Design Lab Course .

**Project Proposal:-**
We have proposed to design and implement the Iris flower classification using kNN algorithm on FPGA that would take features of a flower as input. Implementation
is done in pipelining manner to improve performance.

**Iris Flower classification using KNN:**
The features that are taken as input for classification are sepal length, sepal width,petal length and petal width.Each of these features are different for different classes of iris flowers(setosa, versicolour,virginica).The measurements are real numbers represented in unsigned fixed-point format Q3.13
and the attributes are represented as 2-bit integers (00 – setosa, 01 – versicolor, 10 –virginica). The distance metric for the KNN algorithm is the square of the Euclideandistance and the implementation can be configured to produce results for k = 1, 3 or 5.

**First step :**
Calculate the distance between the new instance(the one we are trying to classify) and the respective training instance from each instance of the training dataset, inserting the result into a list of size k in ascending order. 

1.For the first step, the calculation of the square of the euclidean distance can be made by using the 4 subtractors, 4 multipliers and 3 adders in the design
with 3 pipeline stages in order to reduce the circuits critical path.

2.Here we are finding square of the distance between the new instance and the instance of the training dataset because it requires the additional square root
operation on it which doesn’t require for the comparision of the distances.

3.After obtaining the new instance distance, there are 5 comparators to compare this value with the 5 values from the ascending sorted list.

4.The results of the comparators goes to a priority encoder,which determines if the new distance going to the list(i.e. if the value is lower than atleast one
value of sorted list) and how many right shifts is necessary in order to insert the new distance into the list.

5.It is important to highlight that, in order to keep the coherency between the new instance and its respective class, there is another list of classes which
suffers the same right shifts as the distance list.
