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

<br>

> ###  Fourth    Video Code 
> > ####   Learn about  conrs 

<details>
<summary> what  is Cors </summary>
 Cross-Origin Resource Sharing (CORS) হল একটি HTTP-header ভিত্তিক প্রক্রিয়া যা সার্ভারকে তার নিজের ছাড়া অন্য কোন উৎপত্তি (ডোমেইন, স্কিম বা পোর্ট) নির্দেশ করতে দেয় যেখান থেকে ব্রাউজারকে সম্পদ লোড করার অনুমতি দেওয়া উচিত। CORS এমন একটি পদ্ধতির উপরও নির্ভর করে যার মাধ্যমে ব্রাউজার  Cross-Origin Resource হোস্ট করা সার্ভারের কাছে "preflight" অনুরোধ করে, যাতে সার্ভার প্রকৃত অনুরোধের অনুমতি দেয় কিনা তা পরীক্ষা করে। সেই preflight ব্রাউজারটি হেডার পাঠায় যা HTTP পদ্ধতি নির্দেশ করে এবং শিরোনামগুলি যা প্রকৃত অনুরোধে ব্যবহৃত হবে।
</details>

<details>
<summary> what  is Scheema </summary>
In mongoose একটি schema একটি নির্দিষ্ট নথির কাঠামোর প্রতিনিধিত্ব করে, সম্পূর্ণ বা নথির একটি অংশ। এটি প্রত্যাশিত বৈশিষ্ট্য এবং মান পাশাপাশি সীমাবদ্ধতা এবং সূচক প্রকাশ করার একটি উপায়। একটি মডেল ডাটাবেসের সাথে ইন্টারঅ্যাক্ট করার জন্য একটি প্রোগ্রামিং ইন্টারফেস সংজ্ঞায়িত করে (read, insert, update, etি)
</details>


> ## Install Cors 
>
>> npm install cors
>> 
>> Use server.js
>>> app.use(cors())


> ###  Fourth    Video Code 
> > ####  Mongoose 
<details>
<summary> what  is Mongoose </summary>
 Mongoose হল MongoDB এবং Node এর জন্য একটি অবজেক্ট ডেটা মডেলিং (ODM) লাইব্রেরি। js এটি ডেটার মধ্যে সম্পর্ক পরিচালনা করে, স্কিমা যাচাইকরণ প্রদান করে এবং কোডে বস্তু এবং মঙ্গোডিবিতে সেই বস্তুর প্রতিনিধিত্বের মধ্যে অনুবাদ করতে ব্যবহৃত হয়
</details>

> ####  Mongoose Intall 
>   npm install mongoose --save
>  >// getting-started.js
> > > const mongoose = require('mongoose'); <br>
> > > mongoose.connect('mongodb://localhost:27017/test');

### Server.js File Code 
```
const mongoose  = require('mongoose')
mongoose.connect('mongodb://localhost:27017/contact-db');

const db = mongoose.connection;

db.on('error', (err) => {
console.log(err);
})

db.once('open',() =>{
    console.log('Database connection Established')
})


// sechemma create 
const Schema =  mongoose.Schema;
const demoScheema  = new Schema({
    name:{
        type:String,
        required:true,
        minlength:3
    },
    phone:{
        type:String,
        required:true
    }
})

const Demo = mongoose.model('Demo',demoScheema)



app.get('/demo', (req,res)=>{
    const demo  = new Demo({
        name:"kamrul hasan1",
        phone:"01929394262"
    })
    demo.save()
    .then(data=>{
        res.json({data})
    })
    .catch(err => console.log('error data '))
});


app.get('/get',(req,res)=>{
    Demo.find()
    .then(data =>{
        res.json(data)
        .catch(error => console.log(error))
    })
})


```

























