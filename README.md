angular commands:
npm uninstall -g @angular/cli
npm install -g @angular/cli@17
ng new projectname --no-standalone
cd projectname
ng serve

#angular event binding
#app.component.ts
import { Component } from '@angular/core';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent {
  count = 0;
  increase() {
    this.count++;
  }
}
#app.component.html
<h2>Event Binding</h2>
<button (click)="increase()">Click Me</button>
<p>Count = {{count}}</p>



#Angular Two-Way Binding
#app.component.ts
import { Component } from '@angular/core';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent {
  name = '';
}
#app.component.html
<h2>Two Way Binding</h2>
<input [(ngModel)]="name">
<p>{{name}}</p>
app.module.ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';
import { AppComponent } from './app.component';
@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule,FormsModule ],
  bootstrap: [AppComponent]
})
export class AppModule { }


#Angular Interpolation + Property Binding + Class Binding
#app.component.ts
import { Component } from '@angular/core';
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html'
})
export class AppComponent {
  name = "Siddharth";
  color = true;
}
#app.component.html
<h2>{{name}}</h2>
<input [value]="name">
<p [class.red]="color">Hello Angular</p>
#styles.css
.red{
  color:red;
}


#node js commands 
node projectname.js
#Nodejs Event and callbacks
const events = require('events');
const eventEmitter = new events.EventEmitter();
function display() {
    console.log("Event Triggered");
}
eventEmitter.on('message', display);
eventEmitter.emit('message');


#NodeJs  query string
const http = require('http');
const url = require('url');
http.createServer((req, res) => {
    const q = url.parse(req.url, true).query;
    res.writeHead(200, {'Content-Type':'text/html'});
    res.write("Name = " + q.name);
    res.end();
}).listen(3000);
console.log("Server Running...");
#to run this
"http://localhost:3000/?name=xyz"


#NodeJS file operations
const fs = require('fs');
fs.writeFileSync('demo.txt', '\nHello NodeJS');
console.log("File created");
fs.appendFileSync('demo.txt', '\nWelcome');
console.log("file appended");
console.log("File content:");
console.log(fs.readFileSync('demo.txt', 'utf8'));
if (fs.existsSync('demo.txt')) {
    fs.renameSync('demo.txt', 'newdemo.txt');
    console.log("File renamed");
}
if (fs.existsSync('newdemo.txt')) {
    fs.unlinkSync('newdemo.txt');
    console.log("File deleted");
}



express commands:
npm install express
npm -v,node-v
node project.js
#Express Route Parameters
const express = require('express');
const app = express();
app.get('/student/:name', (req, res) => {
    res.send("Student Name : " + req.params.name);
});
app.listen(3000, () => {
    console.log("Server Running...");
});
#to run this
http://localhost:3000/student/xyz



react commands:
npx create-react-app projectapp
cd projectapp
npm start
#react functional and class Components
import React,{Component}  from "react";
function FuncComp(){
  return<h2>Functional Component</h2>
}
class ClassComp extends Component{
  render(){
    return <h2>Class Component</h2>
  }
}
function App(){
  return(
    <div>
      <FuncComp />
      <ClassComp />
    </div>
  );
}
export default App;


#react states and props
import React, { useState } from 'react';
function Child(props) {
  return <h2>Hello {props.name}</h2>;
}
function App() {
  const [name] = useState("Siddharth");
  return (
    <div>
      <Child name={name} />
    </div>
  );
}
export default App;



#mongodb CRUD operations
mongosh
use college
db.student.drop()
db.student.insertOne({
    roll: 1,
    name: "Siddharth",
    branch: "CSE"
})
db.student.find()
db.student.updateOne(
    { roll: 1 },
    { $set: { branch: "AIML" } }
)
db.student.find()
db.student.deleteOne({ roll: 1 })
db.student.find()


#mongoDB count,limit,sort,skip
mongosh
use college
db.student.drop()
db.student.insertMany([
    { roll: 1, name: "Ram" },
    { roll: 2, name: "Sam" },
    { roll: 3, name: "Tom" },
    { roll: 4, name: "John" }
])
// Count
db.student.countDocuments()
// Limit
db.student.find().limit(2)
// Sort 
db.student.find().sort({ roll: -1 })
// Skip
db.student.find().skip(2)
