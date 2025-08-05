**Day1
Write a program that takes an integer number as input and converts it into its English words representation.** 
1.The program should handle numbers from 0 up to 999,999,999. 
     For example, the input 12345 should output "twelve thousand three hundred forty-five".  
     
Test Case 1:
Input: 105
Output: "one hundred five"

Test Case 2:
Input: 56945781
Output: "fifty-six million nine hundred forty-five thousand seven hundred eighty-one"


**Intuition**
-->In the recursive approach, we break down the number into smaller parts based on place values such as ones, tens, hundreds, thousands, millions, and so on.

-->We start with the largest place value and proceed downward. For example, with the number 1234567, we first handle the millions part (1 Million).

-->We use a helper function that recursively breaks down the number. If the number is less than 10, we return the corresponding word from a predefined list (belowTen). For numbers less than 20, we use another list (belowTwenty) due to their unique names.

-->For numbers below 100, we combine the word for the tens place (from belowHundred) with the word for the ones place, using further recursive calls. For numbers below 1000, we break the number into hundreds and the remainder, processing each part recursively.

-->For larger numbers like 1234567, the function handles the millions part (1 Million), then the thousands (234 Thousand), and finally the hundreds and smaller units (567). Each chunk is processed using recursive calls, building the final English representation from smallest to largest units.

**The recursive function works as follows:**

**Base Case**: For numbers less than 10, the function directly maps to a word using belowTen. For numbers between 10 and 19, belowTwenty handles these unique cases. For numbers between 20 and 99, it combines words from belowHundred for tens and recursively processes the remainder for units.
Recursive Case: For numbers 100 and above, the function processes hundreds, thousands, millions, and billions by breaking the number into smaller parts. For example, for 1234567, it processes the millions part (1 Million), then the thousands part (234 Thousand), and finally the remainder (567). Each part is processed recursively to ensure accurate conversion.
After processing each chunk, we combine the results, handling the hierarchical structure from the smallest unit up to the largest (like billions), ensuring that each segment is correctly represented in English.

**Algorithm**
Initialize arrays to store words for different ranges of numbers:

belowTen for numbers 1-9.
belowTwenty for numbers 10-19.
belowHundred for multiples of ten from 20-90.
Define the main function numberToWords to handle the conversion:

If the number is zero, return "Zero".
Otherwise, call the helper function convertToWords to start the conversion process.
Implement the helper function convertToWords to convert numbers to words recursively:

Base Case 1: Numbers less than 10:
Return the corresponding word from belowTen.
Base Case 2: Numbers less than 20:
Return the corresponding word from belowTwenty.
Numbers from 20 to 99:
Combine the word for the tens place from belowHundred with the recursive result for the units place.
Numbers from 100 to 999:
Combine the recursive result for the hundreds place with "Hundred", and the recursive result for the remaining part.
Numbers from 1000 to 999,999:
Combine the recursive result for thousands with "Thousand", and the recursive result for the remaining part.
Numbers from 1,000,000 to 999,999,999:
Combine the recursive result for millions with "Million", and the recursive result for the remaining part.
Numbers 1,000,000,000 and above:
Combine the recursive result for billions with "Billion", and the recursive result for the remaining part.


**Complexity Analysis**
Let N be the number.

**Time complexity: O(logN)**

The time complexity is O(log 10N) because the number of recursive calls is proportional to the number of digits in the number, which grows logarithmically with the size of the number.

**Space complexity: O(logN)**

The space complexity is O(log 10N), mainly because of the recursion stack. Each recursive call adds a frame to the stack until the base case is reached, leading to space usage proportional to the number of digits in the number.


