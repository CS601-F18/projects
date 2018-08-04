Project 0 - Data Analysis and Java Practice
===========================================

### Due - Tuesday August 28, 2018 - 5pm

For this project, you will implement a data processing program that will perform some basic data analysis on a movie review dataset. You will open and process the input file and save your results to an output file. Your output will be compared to the expected output as part of the grading process. To receive full credit for the test cases your output must *match exactly*.

If you have not already, it is *extremely strongly* advised that you complete the [Easy Practice](https://github.com/CS601-F18/practice.easy) assignment. It contains information about how to correctly set up your development environment for the projects in this course. Before you ask the instructor or TA questions about set up make certain you have make a solid attempt at completing the easy practice assignment.

## Requirements

1. Download the file `movies.txt` from the following URL and save it in the top level of your project directory with the name `movies.txt`: [https://snap.stanford.edu/data/web-Movies.html](https://snap.stanford.edu/data/web-Movies.html) Make sure that you do not attempt to commit this file to github as it is too large!
2. Your program will take as input the following arguments: `-input <input file name> -output <output file name>`. The `-input` and `-output` are flags indicating the following items are the input and output files respectively. A complete example execution follows: `java cs601.project0.AmazonReviews -input movies.txt -output output.txt`.
3. Your program will calculate the following three items: 
  - User IDs of the users with the largest number of reviews (field `review/userId`)
  - Product IDs of the products with the largest number of reviews (field `product/productId`)
  - Product IDs of the products with the highest *average* score (field `product/productId`)
4. The output of your program will be saved to the file specified in the `-output` argument. The format of the file must *exactly* match the expected output. For each item mentioned in #3, your output will have a header as specified below, followed by a list of IDs.  Each ID will be on a separate line and will be preceded by a tab. The list of IDs will be sorted in lexicographical order (the default ordering for Java `String` objects). Below is an abbreviated example.

```
Users with largest number of reviews:
        A16CZRQL23NOIW
Products with largest number of reviews:
        B002QZ1RS6
Products with the highest average score:
        0001501348
        0001516035
        0001517791        
```
   

## Hints

1. Make sure to specify the `Charset` as "ISO-8859-1" when opening the input file.
2. Practice good design! Part of your grade will depend upon the design of your solution and code style. 
3. Consider creating your own test file with a (much!) smaller subset of the input. 
4. You are *strongly* advised to create your own test code to test individual methods and other, smaller, test cases.
5. *DO NOT* make any changes to the test cases provided. You will be expected to pass the tests exactly as they are specified.
6. The web page from which you will download the input data specifies the format of the file. :warning: *Some fields may span multiple lines (example below)!* Do not assume that every record is the same number of lines.

```
review/profileName: nancy "crzyfnyfrog
I love my purple pigtails."
```

## Submission

1. Use the following link to create your private github repository for this assignment: [Project 0](https://classroom.github.com/a/OfX8D3ZS)
2. For full credit, make sure to follow all [Style Guidelines](https://github.com/CS601-F18/notes/blob/master/admin/style.md). Points will be deducted for each violation.
3. All code must be submitted to your github repository by **Tuesday August 28, 2018 - 5pm**.


## Grading Rubric

| Points | Criterion |
| ------ | -------- |  
| 60 | **Functionality** - Passes AmazonReviewsTest test case as required. |  
| 15 | **Design** - Solution is well designed and uses appropriate class and method decomposition. |  
| 15 | **Design** - Solution is efficient and uses appropriate data structures and avoids unnecessary iterations over the data. |  
| 10 | **Design** - Meets all style guidelines. |  

Partial credit *may* be awarded for partial functionality and/or partially correct design or style elements.

## Academic Dishonesty

Any work you submit is expected to be your own original work. If you use any web resources in developing your code you are strongly advised to cite those resources. The only exception to this rule is code that is posted on the class website. The URL of the resource you used in a comment in your code is fine. If I google even a single line of uncited code and find it on the internet you may get a 0 on the assignment or an F in the class. You may also get a 0 on the assignment or an F in the class if your solution is at all similar to that of any other student.

