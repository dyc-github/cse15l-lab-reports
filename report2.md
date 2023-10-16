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

A: The uri contains the query s=Hello

<img width="1512" alt="Screenshot 2023-10-16 at 11 43 59 AM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/6a49118e-6377-4a5d-b172-39ed740d5442">

Q: Which methods in your code are called?

A: main in the StringServer class is called and handleRequest in the Handler class.

Q: What are the relevant arguments to those methods, and the values of any relevant fields of the class?

A: The handleRequest method takes in a URI, the value of which is new URI("http://localhost:2343/add-message?s=How are you"). The main class takes in an array of strings that contains value of the port number of our server.

Q: How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

A: The uri contains the query s=How are you

## Part 2
Q: The path to the private key for your SSH key for logging into ieng6 (on your computer or on the home directory of the lab computer)

Path to my private key:
<img width="365" alt="Screenshot 2023-10-16 at 4 47 20 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/9d748292-f451-4c42-b65e-0ffbd197f3f3">

Q: The path to the public key for your SSH key for logging into ieng6 (within your account on ieng6)

Path to my public key:
<img width="354" alt="Screenshot 2023-10-16 at 4 49 57 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/7b41e80f-1463-4a9c-8ce4-f5f41f08c3b9">

Q: A terminal interaction where you log into ieng6 with your course-specific account without being asked for a password.
<img width="836" alt="Screenshot 2023-10-16 at 4 51 15 PM" src="https://github.com/dyc-github/cse15l-lab-reports/assets/45525219/ef971ea2-02b2-4852-8229-6a54a1fc9dbf">

## Part 3
Something I learned in week 2 was how to connect to remote servers using ssh. I had only used ssh in refrence to ssh keys for github but now know how to access remote terminals using ssh and a URI. 
