# NodeHandson-3

const express = require('express');

const app = express();

const middlewareOne = (req,res,next) => {
    console.log("My first Middleware");
    next();
}

const middlewareTwo = (req,res,next) => {
    console.log("My Second middleware");
    next();
}

app.get('/',(req,res) =>{
    res.send("level1");
})

app.get('/About',(req,res) => {
    res.send("level2");
})

app.get("/contact",middlewareTwo,(req,res) => {
    res.send("This is contact us page");
})

app.get("/author",middlewareTwo,(req,res) => {
    res.send("Author name: Arpana");
})

app.listen(8000,() => {
    console.log("Server running...");
})
