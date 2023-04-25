# Part 1
`public class StringServer {`

    `private StringBuilder runningString = new StringBuilder();

    @GetMapping("/add-message")
    public String addMessage(@RequestParam(value = "s", defaultValue = "") String message) {
        if (!message.isEmpty()) {
            runningString.append("\n").append(message);
        }
        return runningString.toString().trim();
    }`
`}`


# Part 2 
The issue with ReverseInPlace's bug is that it swaps an index that requires modification with an index that has already been altered, resulting in an incorrect output like `[1,2,3]` becoming `[3,1,3]`.   
An input that that gave the correct output was `[1, 1]`

This input gave an error.
`@Test
 public void testReversed1() {
  int [] input1 = {1, 2, 3};
  assertArrayequals(new int[] {3, 2, 1}, ArrayExamples.reversed(input1));`
  
This input outputed correctly.
`@Test
 public void testReversed1() {
  int [] input1 = {1, 1};
  assertArrayequals(new int[] {1, 1}, ArrayExamples.reversed(input1));`
 
In order to fix this bug we created a temporary variable to store the values.
`int temp = arr[i]; 
arr[i] = arr[arr.length - i - 1]; 
arr[arr.length - i - 1] = temp;`

![Image](CSE-15L-Part2-Code.png)


# Part 3
I learned during lab how to debug code efficiently and write test cases to find where the problem lies in the code.
We saw that even if the cdoe works for some test cases that doesn't mean it works for all inputs. 
We need to try many scnenarios that will display a possible wrong output, which can help us find if there is a bug or not.
