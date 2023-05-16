# Curl Advance   https://www.booleanworld.com/curl-command-tutorial-examples/


## Port checking with curl command 

    curl telnet://<host>:<port>

### http request 

    curl http://www.facebook.com/

### redirect  -L flag in command 
  
    curl -L http://www.facebook.com

### Viewing response headers with cURL flag -i 

    curl -L -i http://www.facebook.com/
![image](https://user-images.githubusercontent.com/53860717/143516563-bc224fc4-9f13-43c3-ac1e-5fff3bdedf10.png)

### Viewing request headers and connection details -v 

     curl -v https://www.booleanworld.com/
     
![image](https://user-images.githubusercontent.com/53860717/143516767-b6215ad6-8947-424f-9b46-b678fc92d6eb.png)

### Most often, we aren’t interested in the response body. You can simply hide it by “saving” the output to the null device, which is /dev/null on Linux and MacOS and NUL on Windows:
        curl -vo /dev/null https://www.booleanworld.com/ # Linux/MacOS
        curl -vo NUL https://www.booleanworld.com/ # Windows
        
