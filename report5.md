# Lab Report 5

## Part 1
**1. The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don’t actually make the post! Just write the content that would go in such a post)**

HELP! I don’t know what’s wrong but my bash script isn’t working for some reason. 

My bash script is supposed to print “failed to compile error code: …” when theres an error in Main.java and “no errors good job!” when there isn’t. However as you can see in the screenshot below that clearly isn’t the case.

<img width="682" alt="1" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/54ab13b0-d7a6-4700-9f62-994106ed0636">

<img width="507" alt="2" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/e6563fad-9c04-4a10-8225-a1feb70cd132">

Here is my shell script. Did I do something wrong with the if statement?

<img width="505" alt="3" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/6b57c616-4044-4a69-a953-5939b16f9751">

**2. A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)**

A good first step to take here is to print what the `responseCode` actually is that might give you hints as to what is going wrong. Feel free to ask more questions if you are still confused.

Pay close attention to what `$?` is actually returning the error code of.

**3. Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.**

OHHHH, I see. After printing out $? I can see that the response code is 0. 

<img width="717" alt="4" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/bc3941dd-a854-401b-a964-3f4e641800b3">

<img width="710" alt="5" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/7de7af91-e3ae-4abb-a107-e5942fb87251">

**4. At the end, all the information needed about the setup including:**
- _The file & directory structure needed_

All that’s needed is the Main.java and test.sh files within the lab-report-5 directory. Main.class and output.txt will be generated within the same directory.

<img width="339" alt="6" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/4391091c-47f4-48b2-9218-096cabd9ce9d">

- _The contents of each file before fixing the bug_

Before fixing the bug the contents of Main.java and test.sh look as follows:
```
public class Main {
        public static void main(String[] args){
        int[] arr = new int[]{1, 2, 3, 4, 5};
                for (int i = 0; i <= 25; i++){
                    System.out.println(arr[i]);
                }
        }
}
```
```
javac Main.java
output='java Main'
responseCode=$?
if [[ $responseCode -eq 0 ]]
then
        echo "no errors good job!" 
        $output > output.txt
        exit
else
        echo "failed to compile error code: " $responseCode
fi
```
        
- _The full command line (or lines) you ran to trigger the bug_

The command that triggered the bug is bash ```test.sh```. This will also create Main.class and test.sh.

- _A description of what to edit to fix the bug_

There are a couple ways to fix this bug. The naive way is to just run java Main twice (once for the error code and once for the output):

```
javac Main.java
java Main
responseCode=$?
output='java Main'
if [[ $responseCode -eq 0 ]]
then
    echo "no errors good job!" 
    $output > output.txt
    exit
else
    echo "failed to compile error code: " $responseCode
fi
```
  
<img width="756" alt="7" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/1ec12321-0489-43a6-b0f0-0caf598a1336">

The better way to do it is to preserve the exit code status by wrapping our command with $(). I learned this from this [stack overflow post](https://superuser.com/questions/363444/how-do-i-get-the-output-and-exit-value-of-a-subshell-when-using-bash-e). This way we can avoid running our program if it takes a long time.

```
javac Main.java
output=$(java Main)
responseCode=$?
if [[ $responseCode -eq 0 ]]
then
    echo "no errors good job!" 
    $output > output.txt
    exit
else
    echo "failed to compile error code: " $responseCode
fi
```

<img width="789" alt="8" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/e1f14c22-3b16-49d7-8dd7-8d7ecc39359e">

## Part 2
I think the most neat part of the second half of this quarter has been bash scripting. While I’ve known about bash for a while, I’ve never actually used it. I can see how practical it would be, especially when you have some repetitive work to do like auto grading or even just renaming files over and over. I probably will use bash to help organize my resume files. A lot of the time when I finish a new version of my resume, I need to rename it, delete the blank pages that are added by google drive, and more. I’m not sure if bash will be able to do the pdf editing but I’d like to mess around with it and find out.
