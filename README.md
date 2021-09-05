# Rest Api Tutirial by Hm Nayeem vai 

> ###  First Video Code 


#### Server.js file 
```javasript
const express = require('express') // import express

const  app = express()  //application create 

const  PORT  = process.env.PORT || 3000

app.get('/', (req, res) =>{
    res.send("Hi, My name is kamrul hasan  ")
})


app.listen(PORT, () =>{
    console.log(`server port is ${PORT}`);
})
```



####  Packege.json file Code 
```
 "start": "nodemon server.js"
```





















