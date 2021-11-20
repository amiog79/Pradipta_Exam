# Pradipta_Exam
<html lang="en">
<head>
<meta charset="UFT-8">
<meta name="viewport"
content="width=device-width, 
initial-scale=1.0">

<link rel="stylesheet" href="menu.css">
<link rel="stylesheet" href="layout.css">

<style>
    
h1{
    color: red;
    font-size: 25px;
}

h2{
    color: #17D4FE;
    font-size: 20px;
    background: black;
}

h4{
    color: white;
    background: red;
}

div{
    color: yellow;
    font-size: 25px;
    background: lightgreen;
}

button {
  background: yellow;
  box-shadow: 0 16px 20px 0 rgba(0,0,0,0.2);
  transition: 1s;
  width: 70%;
  height:30%;
  box-sizing:60px;
  float:middle;
  font-size: 50px;
  text-align: center;
  float:;
}

button:hover {
  box-shadow: 0 22px 22px 0 rgba(0,0,0,1.5);
  color:white;
  background:red;
}

.container {
  padding: 8px 16px;
}


var{
    font-size: 60px;
}

marquee{

    color: yellow;
    background: blue;
    font-size: 25px;
}

img{
    border: 10px solid red;
}

tr{
    color: yellow;
    background: blueviolet;
}

td{

    background: blueviolet;
}
    
audio{
    background: blue;
}    

</style>


<script>
var pos = 0, test, test_status, question, choice, choices, chA, chB, chC, correct = 0;

var questions = [
        [ "Which of the following a is not a keyword in Java ?", "class", "interface", "extends", "C" ],

    [ "Which of the following is an interface ?", "Thread", "Date", "Calender", "A" ],

    [ "Which company released Java Version 8 ?", "Sun", "Oracle", "Adobe", "A" ],

    [ "What is the length of Java datatype int ?", "32 bit", "16 bit", "None", "C" ],

    [ "What is the default value of Java datatype boolean?","true","false","0", "A"],

    [ "Which of the following is not an example of DBMS?", "MySQL","Microsoft Acess","Google", "C"],

    [ "How many children does a binary tree have?", "2","any number of children","0 or 1 or 2", "C"],

];

function _(x){
    return document.getElementById(x);
}

function renderQuestion(){
    test = _("test");

    var showscore=Math.round(correct/questions.length*100);


    if(pos >= questions.length){
        document.getElementById("online_start").src = "exam2.jpeg";

        test.innerHTML = "<h3>You got "+correct+" correct of "+questions.length+" questions</h3>";
        test.innerHTML += "<h3> Your Grade : "+showscore +"% </h3>";
        test.innerHTML +="<h4>Exam Finished in Time:" + sec+" Seconds</h4>";
        //test.innerHTML += "<button onclick='EndExam()'>SUBMIT</button>";
        _("test_status").innerHTML = "<h3>Test Completed</h3>";
        pos = 0;
        correct = 0;



        clearTimeout(tim);
        //document.getElementById("endtime").innerHTML = "<h4>Finished Time:"+min+" Minutes :" + sec+" Seconds</h4>";
        document.getElementById("starttime").style.display += 'none';
        document.getElementById("showtime").style.display += 'none';
        //document.getElementById("showtime").style.display += 'block';


        return false;
    }
    _("test_status").innerHTML = "<h3>Question "+(pos+1)+" of "+questions.length+"</h3>";
    question = questions[pos][0];
    chA = questions[pos][1];
    chB = questions[pos][2];
    chC = questions[pos][3];
    test.innerHTML = "<h3>"+question+"</h3>";
    test.innerHTML += "<input type='radio' name='choices' value='A'> "+chA+"<br>";
    test.innerHTML += "<input type='radio' name='choices' value='B'> "+chB+"<br>";
    test.innerHTML += "<input type='radio' name='choices' value='C'> "+chC+"<br><br>";

    test.innerHTML += "<button onclick='checkAnswer()'>Next</button><br><br>";


}

function checkAnswer(){
    choices = document.getElementsByName("choices");
    choice=-1;
    for(var i=0; i<choices.length; i++){
        if(choices[i].checked){
            choice = choices[i].value;
        }
    }
    if(choice == questions[pos][4]){
        correct++;
    }
    pos++;
    renderQuestion();
}

window.addEventListener("load", renderQuestion, false);



function EndExam(){

location.href="Loginpage.htm";
}


    var tim;
       var showscore=Math.round(correct/questions.length*100);
        var min = 1;
        var sec = 60;
        var f = new Date();
        function starttime() {
            showtime();
            document.getElementById("starttime").innerHTML = "<h4>You started your Exam at " + f.getHours() + ":" + f.getMinutes()+"</h4>"; 
        }
        function showtime() {
            if (parseInt(sec) > 0) {
                sec = parseInt(sec) - 1;
                document.getElementById("showtime").innerHTML = "Your Left Time is :=  "+min+" Minutes :" + sec+" Seconds";
                tim = setTimeout("showtime()", 1000);
            }
            else {
                if (parseInt(sec) == 0) {
                    min = parseInt(min) - 0;
            document.getElementById("showtime").innerHTML = "Your Left Time is :=  "+min+" Minutes :" + sec+" Seconds";
                    if (parseInt(min) == 0) {
                        clearTimeout(tim);
            alert("Your Examination Time Up");


            _("test_status").innerHTML = "Test Completed";
            test.innerHTML = "<h2>You got "+correct+" of "+questions.length+" questions correct</h2>";
            test.innerHTML = "<h2>You got "+showscore +"% out of "+questions.length+"</h2>";
            //test.innerHTML = "<button onclick='EndExam()'>SUBMIT</button>";
            
            pos = 0;
            correct = 0;
            clearTimeout(tim);
            document.getElementById("endtime").innerHTML = "You Finished exam at Time is :" + min+" Minutes :" + sec+" Seconds";
            document.getElementById("starttime").style.display += 'none';
            document.getElementById("showtime").style.display += 'none';
            //document.getElementById("showtime").style.display += 'block';
            return false;

                        window.location.href = "Loginpage.htm";
                    }
                    else {
                        min = 0;
                        sec = 60;
                        document.getElementById("showtime").innerHTML = "Your Left Time is : " + min + " Minutes : " + sec + " Seconds ";
                        tim = setTimeout("showtime()", 1000);
                    }
                }

            }
        }





</script>




</head>

<body onload="starttime()" >



<div id="Holder">
<div id="Header"></div>
<div id="NavBar">
<nav>
<ul>

</ul>

<!--DIGITALCOLOR CLOCK-->

<!-- Created By CodingNepal -->
<html lang="en" dir="ltr">
   <head>
      <meta charset="utf-8">
      <title>Digital Clock with Glowing Effect | CodingNepal</title>
      <link rel="stylesheet" href="style.css">
   </head>
   <body>
      <div class="wrapper">
         <div class="display">
            <div id="time" style="color:white; text-align: center; font-size: 50px; background: red; 
                   font-family: sans-serif; border: 10px solid black; "></div>
         </div>
         <span></span>
         <span></span>
      </div>
      <script>
         setInterval(()=>{
           const time = document.querySelector(".display #time");
           let date = new Date();
           let hours = date.getHours();
           let minutes = date.getMinutes();
           let seconds = date.getSeconds();
           let day_night = "AM";
           if(hours > 12){
             day_night = "PM";
             hours = hours - 12;
           }
           if(seconds < 10){
             seconds = "0" + seconds;
           }
           if(minutes < 10){
             minutes = "0" + minutes;
           }
           if(hours < 10){
             hours = "0" + hours;
           }
           time.textContent = hours + ":" + minutes + ":" + seconds + " "+ day_night;
         });
      </script>
   </body>
</html>
<!--END CLOCK-->


<div id="Content">
<div id="PageHeading">
<h1><marquee direction="right" behavior="alternate">All the Best</marquee></h1>
</div>

<div id="ContentLeft">

<img id="online_start" src="exam.png">
<br>
<h2 style="font-size:20px;">>Online Examination System(OES) is a Multiple Choice Questions(MCQ) based 
examination system that provides an easy to use environment for both 
Test Conducters and Students appearing for Examination.</h2>
</div>
 <div id="ContentRight">
<section class="loginform_cf">
<table>
    <tr>
          <td id="test_status"  style="text-align:left" ></td>
          <td id="starttime"    style="text-align:right"></td>
    </tr>

    <tr>
    <td id="test" colspan="2"></td>
    </tr>

</table>    

    

<div id="showtime" style="background:navy; width: 100%;"></div>
</section>
</div>

</div>

<a href="SUBMITTED.html"><button>SUBMIT</button></a>

<div id="Footer" style="background: black; width: 100%;">Website Made by - Pradipta Ghosh</div>

<h2 style="font-size: 30px;">ধুমগড়ের পিশাচ রহস্য</h2>

<!--AUDIO TAG-->

<audio controls>
  <source src="Sunday_Suspense.ogg" type="audio/ogg">
  <source src="Sunday_Suspense.mp3" type="audio/mpeg">
</audio>

<!--END AUDIO TAG-->
    
    
 <!--LIVE WEATHER APP-->


<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Weather App</title>
  <link rel="stylesheet" href="main.css" />
  
  <style>
  
  * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  }
  
  body {
  font-family: 'montserrat', sans-serif;
  background-image: url('bg.jpg');
  background-size: cover;
  background-position: top center;
  }
  
  .app-wrap {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  background-image: linear-gradient(to bottom, rgba(0, 0, 0, 0.3), rgba(0, 0, 0, 0.3));
  }
  
  header {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 50px 15px 15px;
  }
  
  header input {
  width: 100%;
  max-width: 280px;
  padding: 10px 15px;
  border: none;
  outline: none;
  background-color: rgba(255, 255, 255, 0.3);
  border-radius: 0px 16px 0px 16px;
  border-bottom: 3px solid gray;
  
  color: #313131;
  font-size: 20px;
  font-weight: 300;
  transition: 0.2s ease-out;
  }
  
  header input:focus {
  background-color: rgba(255, 255, 255, 0.6);
  }
  
  main {
  flex: 1 1 100%;
  padding: 25px 25px 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  }
  
  .location .city {
  color: #fff;
  font-size: 32px;
  font-weight: 500;
  margin-bottom: 5px;
  }
  
  .location .date {
  color: #fff;
  font-size: 16px;
  }
  
  .current .temp {
  color: #fff;
  font-size: 102px;
  font-weight: 900;
  margin: 30px 0px;
  text-shadow: 2px 10px rgba(0, 0, 0, 0.6);
  }
  
  .current .temp span {
  font-weight: 500;
  }
  
  .current .weather {
  color: #fff;
  font-size: 32px;
  font-weight: 700;
  font-style: italic;
  margin-bottom: 15px;
  text-shadow: 0px 3px rgba(0, 0, 0, 0.4);
  }
  
  .current .hi-low {
  color: #fff;
  font-size: 24px;
  font-weight: 500;
  text-shadow: 0px 4px rgba(0, 0, 0, 0.4);
  }
  
  
  </style>
  
</head>
<body>
  <div class="app-wrap">
    <header style="background:darkcyan;">
      <input type="text" autocomplete="off" class="search-box" placeholder="Search for a city..." style="background:yellow;"/>
    </header>
    <main style="background:darkkhaki;">
      <section class="location" style="background:blue;">
        <div class="city" style="background:blue;">New York, US</div>
        <div class="date" style="background:black;"></div>
      </section>
      <div class="current" style="background:red;">
        <div class="temp" style="background:red;">15<span style="background:red;">°c</span></div>
        <div class="weather" style="background:black;">Sunny</div>
        <div class="hi-low" style="background:black;">13°c / 16°c</div>
      </div>
    </main>
  </div>
  <script src="main.js"></script>
  
 <script>
 
 const api = {
 key: "fcc8de7015bbb202209bbf0261babf4c",
 base: "https://api.openweathermap.org/data/2.5/"
 }
 
 const searchbox = document.querySelector('.search-box');
 searchbox.addEventListener('keypress', setQuery);
 
 function setQuery(evt) {
 if (evt.keyCode == 13) {
 getResults(searchbox.value);
 }
 }
 
 function getResults (query) {
 fetch(`${api.base}weather?q=${query}&units=metric&APPID=${api.key}`)
 .then(weather => {
 return weather.json();
 }).then(displayResults);
 }
 
 function displayResults (weather) {
 let city = document.querySelector('.location .city');
 city.innerText = `${weather.name}, ${weather.sys.country}`;
 
 let now = new Date();
 let date = document.querySelector('.location .date');
 date.innerText = dateBuilder(now);
 
 let temp = document.querySelector('.current .temp');
 temp.innerHTML = `${Math.round(weather.main.temp)}<span>°c</span>`;
 
 let weather_el = document.querySelector('.current .weather');
 weather_el.innerText = weather.weather[0].main;
 
 let hilow = document.querySelector('.hi-low');
 hilow.innerText = `${Math.round(weather.main.temp_min)}°c / ${Math.round(weather.main.temp_max)}°c`;
 }
 
 function dateBuilder (d) {
 let months = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
 let days = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
 
 let day = days[d.getDay()];
 let date = d.getDate();
 let month = months[d.getMonth()];
 let year = d.getFullYear();
 
 return `${day} ${date} ${month} ${year}`;
 }
 
 
 </script> 
  
</body>
</html>


<!--END WEATHER APP-->
   

 <!--VIDEO-->
<video width="500px" height="260px" controls="">
  <source src="DUI_PRITHIBI.mp4" type="video/mp4">
  <source src="mov_bbb.ogg" type="video/ogg">
  Your browser does not support HTML video.
</video>
<!--END VIDEO-->
    

 <center style="font-size:16px;background:red"><u><a style="color:white;">Privacy Policy</a></u> <u><a style="color:white">Terms & Conditions</a></u></center>
<center style= "color:black;font-size:16px;background:#17D4FE">Copyright © By Pradipta Ghosh.com 2019</center>



    
