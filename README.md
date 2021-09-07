# Rest Api Tutirial by Hm Nayeem vai 
> ##  How to Setup  Environment by Rest Api
- ***Express Install:*** npm i express
- ***Nodemon Install:***  npm i -D nodemon 

> ### Third Video 
- ***morgan Install:***  npm install morgan 
- ***bodyParser Install:***   npm install body-parser 
<br>
> ###  First Video Code 
> > ####  S Simple Rest  Api Setupe Example 


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
> ###  Second  Video Code 
> > ####   How to Setup Route in Rest Api

### contact route create file path
 ``` api/routes/contact.js```

 > ### contact.js  Code 
 ```
 const express = require('express');
const router = express.Router();


// contact get router code 
router.get('/',(req, res, next)=>{
    res.status(200).json({
        massage:"This is  contact get  router "
    })
})

// contact post  router code 
router.post('/',(req, res, next)=>{
    res.status(201).json({
        massage:"This is  contact post  router "
    })
})

// contact dynamic router  code 
router.get('/:id',(req, res, next)=>{
    const id  = req.params.id;
    res.json({
        id
    })
})

// put  dynamic router  code 
router.put('/:id',(req, res, next)=>{
    res.json({
        massage:"This is  contact put   router "
    })
})

// put  dynamic router  code 
router.delete('/:id',(req, res, next)=>{
    res.json({
        massage:"This is  contact delete   router "
    })
})

module.exports = router
 ```
 > ##   Add server js   Code 
 ```
 const contactRouter  = require('./api/routes/contacts')
 
app.use('/api/contacts',contactRouter);
 ```

> ###  Third   Video Code 
> > ####   Learn about middleware


## Require file 

> ###  server.js 

```javascript
var bodyParser = require('body-parser')

// parse application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({ extended: true }))

// parse application/json
app.use(bodyParser.json())

app.use(morgan('dev'))

var morgan = require('morgan')

```

> ### contact.js 

```
const express = require('express')
const router = express.Router();

const contacts  = [];

router.get('/', (req, res) => {
    res.status(200).json({
        contacts
    })
})

// post route 
router.post('/', (req, res) => {
    contacts.push({
        name:req.body.name,
        message:req.body.message
    })
   
    res.status(201).json({
        messaget:"saved data "
    })
})


module.exports = router
```
















