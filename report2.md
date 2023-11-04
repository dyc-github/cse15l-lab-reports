# Lab Report 2
## Part 1
The code for my implementation of StringServer.java is below.
```
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    private ArrayList<String> strings = new ArrayList<String>();

    public String handleRequest(URI url) {
        String path = url.getPath();
        if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                    strings.add(parameters[1]);
            }
        }

        if (path.equals("/") || path.equals("/add-message")) {
            String response = "";
            for(int i = 0; i < strings.size(); i++){ 
                response += String.format( "%d. %s\n", i+1, strings.get(i));
            }
            return response;
        }  
        return "404 Not Found!";
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

We can see the results for this code from the following screenshots:
<img width="1510" alt="Screenshot 2023-10-16 at 11 43 29 AM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/a4383723-84ed-4146-8be0-d5452039b9d0">
Q: Which methods in your code are called?

A: main in the StringServer class is called and handleRequest in the Handler class.

Q: What are the relevant arguments to those methods, and the values of any relevant fields of the class?

A: The handleRequest method takes in a URI, the value of which is new URI("http://localhost:2343/add-message?s=Hello"). The main class takes in an array of strings that contains value of the port number of our server.

Q: How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

A: 
```url```  is an argument passed into the handle request method. It will have the value ```new URI("http://localhost:2000/add-message?s=Hello")```.

```strings``` is an arraylist containing a list of all strings previously passed in through /add-message. Prior to /add-message?s=Hello ```strings``` was empty and had the value {}. We append the string "Hello" to this list when we request /add-message?s=Hello. So ```strings``` changes to be a list containing the string "Hello" and will have the value {"Hello"}.

```response``` is a string that formats the strings in ```strings``` as a numbered list. Prior to /add-message?s=Hello response would return as an empty string with value "". After /add-message?s=hello response has value: "1. Hello\n".
<img width="1510" alt="Screenshot 2023-11-04 at 12 28 10 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/ef36b733-f9b1-4357-9c7a-6a3ea9102768">

Q: Which methods in your code are called?

A: main in the StringServer class is called and handleRequest in the Handler class.

Q: What are the relevant arguments to those methods, and the values of any relevant fields of the class?

A: The handleRequest method takes in a URI that contains path "/add-message" and query s=How are you. The variable ```parameters``` is the array {"s", "How are you"}. Since the parameter is s we append our output to global ArrayList ```strings```. We then output the value of ```strings``` which also includes our new query "How are you". 

Q: How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

A: 
```url```  is an argument passed into the handle request method. It will have the value ```new URI("http://localhost:2000/add-message?s=How are you")```.

```strings``` is an arraylist containing a list of all strings previously passed in through /add-message. Prior to /add-message?s=How are you ```strings``` had the value {"Hello"}. We append the string "How are you" to this list when we request /add-message?s=How are you. So ```strings``` changes to be a list containing the string "How are you" and will have the value {"Hello", "How are you"}.

```response``` is a string that formats the strings in ```strings``` as a numbered list. Prior to /add-message?s=How Are You, ```response``` would return as with value "1. Hello\n". After /add-message?s=How are you response has value: 
"1. Hello\n2. How are you\n".
<img width="1199" alt="Screenshot 2023-11-04 at 12 30 19 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/02816ba1-9945-4fbc-9777-45209a88a795">

## Part 2
Q: The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer)

Path to my private key:
<img width="493" alt="Screenshot 2023-11-02 at 11 43 12 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/b9c92136-c28e-43f9-8277-53ef69968d14">

Q: The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6)

Path to my public key:
<img width="603" alt="Screenshot 2023-11-02 at 11 49 09 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/e0bef98c-b749-463b-98b2-18209af21d24">

Q: A terminal interaction where you log into ieng6 with your course-specific account without being asked for a password.
<img width="836" alt="Screenshot 2023-10-16 at 4 51 15 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/ef971ea2-02b2-4852-8229-6a54a1fc9dbf">

## Part 3
Something I learned in week 2 was how to connect to remote servers using ssh. I had only used ssh in refrence to ssh keys for github but now know how to access remote terminals using ssh and a URI. 
