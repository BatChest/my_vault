Created: 2022-03-07 19:22
Status: #idea
Tags:
# Selection Sort
- This a type of sorting algorithm that is an *in-place comparison sort*
- Has O(n$^2$) time complexity, making it inefficient on large files
- The algorithm divides input list into two parts:
sublist of items already sorted, which is build up from left to right at the front of the list, and the sublist of items remaining to be sorted that occupy the rest of the list.
- Initially the sorted sublist is empty and the unsorted sublist is the entire input list.
- Finds the smallest or largest, depending on sorting order element in the unsorted sublist, exchanging (swapping) it with the leftmost unsorted element (putting it in sorted order), and moving the sublist boundaries one element to the right

```ad-example
![[Screenshots/Pasted image 20220307192945.png]]
```

Lets see how this would look when we apply selection sort to the above array
1. First we are going to find the samllest element and place it at position 0.
```ad-example
![[Screenshots/Pasted image 20220307193614.png]]
We do this by starting at the front of the array and comparing two elements at a time and who ever is the smallest we swap their position to the left and continue checking the other elements
![[Screenshots/Pasted image 20220307193432.png]]

```
2. Next we find the smallest element and place it at position 1.
```ad-example
![[Screenshots/Pasted image 20220307193736.png]]
We are basically repeating the same steps like before but instead we are starting at index 1 and comparing the element's value until we find the smallest one. Remember we exclude index 0 since that has already been sorted
```
3. Next we find the smallest element and place it at position 2.
```ad-example
![[Screenshots/Pasted image 20220307193925.png]]
```

4. Next we find the smallest element and place it at position 3.

```ad-example
![[Screenshots/Pasted image 20220307193956.png]]
```

##### Algorithm In code (c++)
We are first going to have two variables
- arr : array of items
- n : size of the list
```ad-note
We are going to have a table updating the variables in our algorithm
![[Screenshots/Pasted image 20220307194323.png]]
```

We are going to start with a for loop since in thr previous example we repeated the same steps four times
```ad-example
![[Screenshots/Pasted image 20220307194538.png]]
Our limit is going to be one less than our size of the list since before we repeated the steps 4 times so we have n - 1.
```

Then we are going to initialize the variable min to keep track of which minimum value we have gone through
```ad-example
![[Screenshots/Pasted image 20220307194835.png]]

As well as our tablbe being updated as well
![[Screenshots/Pasted image 20220307194901.png]]
```

Then we are going into our internal for loop since are going to be looping the same procedure of comparing two index's values so we make another for loop inside our first for loop
```ad-example
![[Screenshots/Pasted image 20220307195052.png]]

Again we are going to update the table as well 
![[Screenshots/Pasted image 20220307195113.png]]

so in the for loop we have $i$ < 5 and we go the next line where we are checking index 1 and index 0 because j = 1 which means we are checking 25 and 64 and 25 < 64 is true.

So know we can declare 25 as our min element and so we update our table
![[Screenshots/Pasted image 20220307195415.png]]
```
We are going to keep  repeating the same steps until we are sure that we have the smallest element in the array.

Once we find the smallest element we can finally have our update table
```ad-example
![[Screenshots/Pasted image 20220307195709.png]]

and lastly we are going to be swapping the elements to finally put them in order.
![[Screenshots/Pasted image 20220307195817.png]]

```
We are going to keep comparing and swapping until we finally have the sorted array.


# References
1. https://www.youtube.com/watch?v=IIcvhrQnySM


