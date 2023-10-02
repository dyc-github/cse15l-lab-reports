# Lab Report 1
This week we learned about cd ls and cat.

## cd
Q: Share an example of using the command with no arguments.

A: Just the cd command will return the user to the root directory. In the example below we are in the ```/home/lecture1/messages``` directory and get sent to the ```/home``` directory.
```
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
[user@sahara ~/lecture1/messages]$ cd
[user@sahara ~]$ pwd
/home
```

Q: Share an exmaple of using the command with a path to a directory as an argument.

A: When you provide a path to the cd command you will be navigated to that directory relative to your current directory. In the example below we are in the ```/home``` and get sent to the ```/home/lecture1/messages``` directory.

```
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ cd lecture1/messages/
[user@sahara ~/lecture1/messages]$ pwd
/home/lecture1/messages
```

Q: Share an example of using the command with a path to a file as an argument.

A: Using cd with a path to a file as an argument you will get an error message notifying the user that the path does not lead to a directory. The reson why we get this error is that we cannot use a file as a directory. In the example below we are in the ```/home``` directory and get an error running ```cd lecture1/messages/ko.txt ``` 

```
[user@sahara ~]$ cd lecture1/messages/ko.txt 
bash: cd: lecture1/messages/ko.txt: Not a directory
```

## ls
Q: Share an example of using the command with no arguments.

A: All files and directories in the current directory will be printed. In the example below we are in the ```/home/lecture/messages``` directory and print the contents of that directory.
```
[user@sahara ~/lecture1/messages]$ ls
en-us.txt  es-mx.txt  ko.txt  zh-cn.txt
```

Q: Share an exmaple of using the command with a path to a directory as an argument.

A: You will print all the files and directories in the directory specified by the path. In the example below we are in the ```/home``` directory and print the contents of the ```/home/lecture/messages``` directory.
```
[user@sahara ~]$ ls lecture1/messages/
en-us.txt  es-mx.txt  ko.txt  zh-cn.txt
```

Q: Share an example of using the command with a path to a file as an argument.

A: Using ls with a path to a file as an argument will result in the terminal printing the path provided. In the example below we are in the ```/home``` directory and print out the path ```lecture1/Hello.java``` .
```
[user@sahara ~]$ ls lecture1/Hello.java 
lecture1/Hello.java
```

## cat
Q: Share an example of using the command with no arguments.

A: Using cat on a command with no arguments, nothing will happen and the command will run forever. We will have to use ctrl + c to terminate the command. In the example we start in the ```/home/lecture1``` directory.
```
[user@sahara ~/lecture1]$ cat

```
Q: Share an exmaple of using the command with a path to a directory as an argument.

A: Using cat with a path to a directory we get a message notifying us that the provided path is a directory. In the example we start in the ```/home/lecture1``` directory.
```
[user@sahara ~/lecture1]$ cat messages/
cat: messages/: Is a directory
```

Q: Share an example of using the command with a path to a file as an argument.

A: Using cat with a path to a file will result in the terminal pringting the contents of the file. In the example below we will start in the ```/home/lecture1``` directory and print the contents of ```Hello.java```.
```
[user@sahara ~/lecture1]$ cat Hello.java 
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}
```
