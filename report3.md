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
I have chosen the ``` find ``` command. 

### ``` -name ``` option
I found out about this command through the [CSE 15L class](https://ucsd-cse15l-f23.github.io/week/week5/). I also found additional notes on [Linuxize's guide on the find command](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/#:~:text=Finding%20files%20by%20name%20is,file%20you%20are%20searching%20for.) for examples. The ```-name``` command allows you to look up files and directories by name.

- Example 1: We can use name to find a file which we know the name of but don't know where exactly in technical it is. 
```
(base) davidchoi@Davids-MacBook-Pro technical % find . -name water_fees.txt 
./government/Media/water_fees.txt
```
- Example 2: We can use find in conjunction with * (which is a wildcard character which represents a place holder) to search for all files that match the pattern of our search.
```
(base) davidchoi@Davids-MacBook-Pro technical % find . -name "Texas*"
./government/Media/Texas_Lawyer.txt
./government/Media/Texas_Supreme_Court.txt
```
### ```-type``` option
I found out about this through [Linuxize's guide on the find command](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/#find-files-by-size). The ```-type``` command helps us filter for certain types of data (for example only directories).
- Example 1:I'm for directories with the letter s but not files.
```
(base) davidchoi@Davids-MacBook-Pro technical % find . -type d -name "*s*"
./government/Alcohol_Problems
./government/Post_Rate_Comm
./plos
```
- Example 2: I want to exlude directories and only want the files. *Note how we exclude the ./911report directory.*
```
find . -type f -name "*report*"
./government/About_LSC/Progress_report.txt
./government/About_LSC/Strategic_report.txt
./government/About_LSC/Special_report_to_congress.txt
./government/About_LSC/commission_report.txt
./government/About_LSC/reporting_system.txt
```

### ```-size``` option
I found out about this through [Linuxize's guide on the find command](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/#find-files-by-size). The ```-size``` command allows us to filter files and directories by size (```+``` includes files greater, ```-``` includes files smaller). This one is interesting as it may help in trying to free up space.
- Example 1: I'm looking for all files greater than 200 kb in size.
```
find . -type f -size +200k
./government/About_LSC/commission_report.txt
./government/Env_Prot_Agen/bill.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./government/Gen_Account_Office/d01591sp.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-3.txt
```
- Example 2: I'm looking for all files less than 1 kb in size.
```
(base) davidchoi@Davids-MacBook-Pro technical % find . -type f -size -1k 
./plos/pmed.0020191.txt
./plos/pmed.0020226.txt
```

### ```-not``` option
We can use the -not option to exclude rather than include certain properties. I once again found out about this through Linuxize's guide on the find command](https://linuxize.com/post/how-to-find-files-in-linux-using-the-command-line/#find-files-by-size) but also through [this stack overflow post](https://stackoverflow.com/questions/1341467/find-filenames-not-ending-in-specific-extensions-on-unix). The ```-not``` command filters by the negation of the command it preceeds. 
- Example 1: Look for all files and directories that don't end with .txt.
```
(base) davidchoi@Davids-MacBook-Pro technical % find .  -not -name "*.txt"
.
./government
./government/.DS_Store
./government/About_LSC
./government/Env_Prot_Agen
./government/Alcohol_Problems
./government/Gen_Account_Office
./government/Post_Rate_Comm
./government/Media
./.DS_Store
./plos
./biomed
./911report
```
- Example 2: Find all files that include ch that do not contain the word chapter and do not contain the word research.
```
find . -name "*ch*" -not -name "*chapter*" -not -name "*research*"
./government/Env_Prot_Agen/tech_sectiong.txt
./government/Env_Prot_Agen/tech_adden.txt
./government/Post_Rate_Comm/Gleiman_EMASpeech.txt
./government/Post_Rate_Comm/Mitchell_spyros-first-class.txt
./government/Post_Rate_Comm/Mitchell_RMVancouver.txt
./government/Post_Rate_Comm/Mitchell_6-17-Mit.txt
./government/Post_Rate_Comm/WolakSpeech_usps.txt
./government/Media/Legal-aid_chief.txt
./government/Media/Law_Schools.txt
./government/Media/AP_LawSchoolDebts.txt
./government/Media/Law-school_grads.txt
./government/Media/Using_Tech_Tools.txt
./government/Media/Low-income_children.txt
```




