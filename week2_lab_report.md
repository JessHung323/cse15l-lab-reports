# Lab Report 2
## Servers & SSH Keys

### Part 1
- Code for `ChatServer`
    - ```
        import java.io.IOException;
        import java.net.URI;

        class Handler implements URLHandler {
            String text = "";

            public String handleRequest(URI url) {
                if (url.getPath().equals("/")) {
                    return String.format("Woops you have no input");
                } else if (url.getPath().equals("/add-message")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].charAt(parameters[0].length()-1) == 's' && parameters[1].split("&")[1].equals("user")) {
                        String message = parameters[1].split("&")[0];
                        String name = parameters[2];
                        text += name + ": " + message + "\n";
                        return text;
                    }
                } else {
                    return "404 Not Found!";
                }
                return "404 Not Found!";
            }
        }

        class ChatServer {
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
    - Using `add-message` for *first* time after launching server:
        - ![/add-message?s=Hello&user=jpolitz](assets/sc1.png)
        - First by launching the server at the port 4000, the main method in the class `ChatServer`is used. The argument for this call is the port number 4000 that I used to launch the server.
        - As the localhost is opened on the webserver, I added `/add-message?s=Hello&user=jpolitz` as a path to the url. This execution changed the class variable `text`, which is a variable that reflects the message on the webpage. The value of this variable changes from an empty string, to a message with `jpolitz: Hello` added to the end, as expected.
    - Using `add-message` for *second* time after launching server:
        - ![/add-message?s=How are you today&user=everyone](assets/sc2.png)
        - After the first execution, I altered the orginal url path to `/add-message?s=How are you today&user=everyone`. This execution changed the class variable `text`, which is a variable that reflects the message on the webpage. The value of this variable isthen updated from the previous message, to a message with 
        ```
        jpolitz: Hello
        everyone: How are you today
        ```
