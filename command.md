Testing REST API using curl
====================
This gist lists only the basic commands to test REST APIs with curl. 
If you need something more advanced, [this book](https://ec.haxx.se/) has everything you may need. 


Simple GET Requests
-----------------------
Display the response only
```
curl http://www.example.com/api/ping
```

Display the headers as well
```
curl -v http://www.example.com/api/ping
```

Save the response to a file
```
curl -o user_3.json http://www.example.com/api/users/3
```

POST/PUT/DELETE Request
-----------------------
Use `-d` to set data, `-X` to mention method

Send form data (default) `application/x-www-form-urlencoded` with POST
```
curl -d 'name=Sugar&category_id=3' http://example.com/api/products
curl -X PUT -d 'name=Sugar&category_id=3' http://example.com/api/products
```
Field values can be mentioned separately.
```
curl -d name=Sugar -d category_id=3 http://example.com/api/products
```

Submit as JSON Request Body
```
curl -d '{"name":"Sugar", "category_id":3}' -H 'Content-Type: application/json' http://example.com/api/products
curl -X PUT -d '{"name":"Sugar", "category_id":3}' -H 'Content-Type: application/json' http://example.com/api/products
```


For windows command prompt, you'd need to replace the single quotes with double quotes and need to escape as `\"` where necessary.
```
curl -d "{\"name\":\"Sugar\", \"category_id\":3}" ...
```

Set Request body from a file
```
curl -d @path/to/data.json -H 'Content-Type: application/json' http://example.com/api/products
curl -X PUT -d @path/to/data.json -H 'Content-Type: application/json' http://example.com/api/products
```

DELETE Request
```
curl -X DELETE http://example.com/api/products/9
```

Custom Headers
-------------------
Use `--header` or `-H` option

```
curl -H 'Accept: application/json' -H 'X-Api-Key: 842be059-5e0b-43c1-bd95-5c7705858b0b' http://example.com/api/resource
```

Authentication
-------------------
Basic Auth
```
curl --user username:password http://example.com/api/resource
```

Access Token
```
curl -H "Authorization: Bearer b1094abc0-54a4-3eab-7213-877142c33fh3" http://example.com/api/resource
```

API Key
```
curl -H 'X-Api-Key: 842be059-5e0b-43c1-bd95-5c7705858b0b' http://example.com/api/resource
```

Urlencode explicitly
--------------------
```
curl -X PUT --data-urlencode "name=John Doe (Junior)" -d category_id=3 http://example.com/api/users/13
```
File contents can be urlencoded too
```
curl --data-urlencode fieldName@contents.txt http://example.com/api/users
```

File Upload
-----------------
Use `-F` to submit as `multipart/form-data`
```
curl -F 'img_avatar=@/home/petehouston/hello.png' -F default=no http://example.com/api/users/13/avatar
```

Multiple files
```
curl -F 'id_page_1=@/path/to/front_side.jpg' -F 'id_page_2=@/path/to/back_side.jpg' http://example.com/api/users/13/photo_id
```

Array of files
```
curl -F 'pages[]=@/path/to/page_1.jpg' -F 'pages[]=@/path/to/page_2.jpg' ... http://example.com/api/books/9/pages
