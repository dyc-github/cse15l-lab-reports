# Lab Report 3
## Part 1 Bugs
I will be using reversed in the ArrayExamples.java file.
```
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```

Q: A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)

A: Below is the jUnit test of the failure inducing input {1, 2, 3, 4} for ArrayExamples.reversed(int[] arr).
```
  //ArrayTests.java
  @Test
  public void testReversed2() {
    int[] input1 = {1, 2, 3, 4};
    assertArrayEquals(new int[]{4, 3, 2, 1}, ArrayExamples.reversed(input1));
  }
```
Q:An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)

A: Below is the jUnit test of the success inducing input {} for ArrayExamples.reversed(int[] arr).
```
  @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
```
Q: The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)

A: The symptom, which is the message we get running the tests is below
<img width="1062" alt="Screenshot 2023-11-02 at 1 44 40 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/a5687104-5a04-48fd-83cf-e16ab46b4f20">

Here is a screenshot of the test file of all tests run.
<img width="829" alt="Screenshot 2023-11-02 at 1 46 19 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/78569d52-8781-46b2-8f19-dae288a3fb61">

Q: The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)

A: Here is the code before the code is fixed:
```
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1]; //<------ the bug is here 
    }
    return arr; //<------ the bug is here and here
  }
```
Terminal output:
<img width="1062" alt="Screenshot 2023-11-02 at 1 44 40 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/a5687104-5a04-48fd-83cf-e16ab46b4f20">


Here is the code after it is fixed:
```
  // Returns a *new* array with all the elements of the input array in reversed
  // order
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```
Terminal output:
<img width="970" alt="Screenshot 2023-11-02 at 1 54 55 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/80390261-4497-4342-9709-a19d284e1a6d">

## Part 2 Researching Commands
