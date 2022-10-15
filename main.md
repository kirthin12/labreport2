# Week 1 Lab Report
## 1. Part 1
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler
{
    public String handleRequest(URI url) 
    {
        ArrayList<String> listOfWords = new ArrayList<String>();
        if (url.getPath().equals("/")) 
        {
            return "main page";
        }
        else if (url.getPath().equals("/print"))
        {
            String list = "";
            for (int i = 0; i < listOfWords.size(); i++)
            {
                list = list + listOfWords.get(i) + " ";
            }
            return list;
        }
        else 
        {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add")) 
            {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) 
                {
                    listOfWords.add(parameters[1]);
                    return "added";
                }
            }
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException 
    {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```


## 2. Part 2
After downloading VScode, open a terminal and enter the following in there:
```
ssh cs15lfa22zz@ieng6.ucsd.edu
```
