# trapping-rain-water
TRAPPING RAIN WATER

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

 

Example 1:


Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.

Example 2:

Input: height = [4,2,0,3,2,5]
Output: 9

APPROACH 1

This is a function to find the trapped water between a set of buildings represented as a list of heights (height). The function takes in a list of integers as an argument and returns an integer as the result.

1. Check if the input list is empty. If it is, return 0.

2. Initialize two lists the_left and the_right of the same length as the input list. These lists will store the highest building to the left and right of each building respectively.

3. Initialize a variable total to store the total trapped water.

4. Fill the first element of the_left with the first element of the input list height. This represents the highest building to the left of the first building.

5. For the rest of the elements in the list height, starting from the second element, fill in the_left such that each element stores the maximum of the previous element and the corresponding element of height.

6. Fill the last element of the_right with the last element of the input list height. This represents the highest building to the right of the last building.

7. For the rest of the elements in the list height, starting from the second last element and counting down, fill in the_right such that each element stores the maximum of the next element and the corresponding element of height.

8. For each element in the list height, add the minimum of the corresponding elements of the_left and the_right to the total trapped water. The trapped water at this point is calculated as min(the_left[i], the_right[i]) - height[i].

9. Return total as the result.

Reasoning:

This code calculates the total amount of water trapped between buildings represented by an array "height".

The algorithm first checks if the input array "height" is empty and returns 0 if it is. Then it initializes two arrays "the_left" and "the_right" with the same length as "height" and all elements equal to 0. "total" is also initialized to 0.

Next, "the_left[0]" is set to the first element of "height". Then, in a for loop, the values in "the_left" are updated such that each element represents the maximum height of the buildings up to that index, i.e., "the_left[i] = max(the_left[i-1], height[i])".

Similarly, "the_right[-1]" is set to the last element of "height" and in another for loop, the values in "the_right" are updated to represent the maximum height of the buildings from that index to the end of the array.

Finally, in a third for loop, the total amount of water trapped between the buildings is calculated. "total" is updated by adding the amount of water trapped at each building represented by the difference between the minimum of the two max heights (from "the_left" and "the_right") and the height of the building. The final result is returned as the "total" value.

TEST CASES
1:   Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]  Output: 6

Reasoning:

1. The first step is to check if the input list is empty or not. If the input is an empty list, the code returns 0.

2. Two lists the_left and the_right of length len(height) are initialized, with all elements set to 0.

3. The first element of the the_left list is set to the first element of the input height list. This value represents the height of the left wall at index 0.

4. A for loop runs from 1 to len(height) to find the maximum height of the left wall for each index i. It sets the_left[i] = max(the_left[i-1], height[i]), where the_left[i-1] is the maximum height of the left wall at the previous index, and height[i] is the current height.

5. The last element of the the_right list is set to the last element of the height list. This value represents the height of the right wall at index len(height) - 1.

6. Another for loop runs from len(height) - 2 to -1, in reverse order, to find the maximum height of the right wall for each index i. It sets the_right[i] = max(the_right[i+1], height[i]), where the_right[i+1] is the maximum height of the right wall at the next index, and height[i] is the current height.

7. Finally, a for loop runs from 0 to len(height) to calculate the total trapped water. The code adds min(the_left[i], the_right[i]) - height[i] to total for each index i. This calculation is done because the amount of trapped water at each index i is equal to the minimum height of the surrounding walls minus the height of the current wall.

8. The code returns the total value, which is the sum of trapped water across all indexes.

So, for the input [0,1,0,2,1,0,1,3,2,1,2,1], the code would return 6, which is the sum of trapped water at each index.


2. Input: height = [4,2,0,3,2,5]  Output: 9

Reasoning:

The algorithm calculates the amount of trapped water in a histogram represented by the input array "height". Here's a step-by-step explanation for the example input [4,2,0,3,2,5]:


1. Initialize two arrays, the_left and the_right, to store the maximum height from the left and the right for each element in the input array height. These arrays have the same length as the input array height.

2. Populate the the_left array with the maximum height from the left for each element in the input array height. Start with the first element height[0], set the_left[0] = height[0]. Then, for each subsequent element height[i], set the_left[i] = max(the_left[i-1], height[i]). After this step, the_left will be equal to [4, 4, 4, 4, 4, 5].

3. Populate the the_right array with the maximum height from the right for each element in the input array height. Start with the last element height[-1], set the_right[-1] = height[-1]. Then, loop through each subsequent element from the end to the beginning, height[i]. For each element, set the_right[i] = max(the_right[i+1], height[i]). After this step, the_right will be equal to [5, 5, 5, 3, 3, 2].

4. Initialize a variable total to store the total amount of trapped water in the histogram. Set total to 0.

5. Loop through each element height[i] in the input array height. For each element, calculate the trapped water by subtracting the height of the element from the minimum of the maximum heights from the left and the right. Add this trapped water to the total. Set total = total + min(the_left[i], the_right[i]) - height[i].

6. Return the total variable, which represents the amount of trapped water in the histogram. In this example, total will be equal to 9.

If you want to see the code enter [here](code)
