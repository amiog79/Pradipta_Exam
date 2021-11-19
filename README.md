# Pradipta_Exam
<!DOCTYPE html>
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
    font-size: 30px;
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
    color: blue;
    font-size: 20px;
    background: lightgreen;
}

button {
  background: yellow;
  box-shadow: 0 16px 20px 0 rgba(0,0,0,0.2);
  transition: 1s;
  width: 50%;
  height:30%;
  box-sizing:60px;
  float:middle;
  font-size: 50px;
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
    font-size: 30px;
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
    
</style>


<script>
var pos = 0, test, test_status, question, choice, choices, chA, chB, chC, correct = 0;

var questions = [
        [ "Which of the following a is not a keyword in Java ?", "class", "interface", "extends", "C" ],

    [ "Which of the following is an interface ?", "Thread", "Date", "Calender", "A" ],

    [ "Which company released Java Version 8 ?", "Sun", "Oracle", "Adobe", "A" ],

    [ "What is the length of Java datatype int ?", "32 bit", "16 bit", "None", "C" ],

    [ "What is the default value of Java datatype boolean?","true","false","0","A"]
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
        test.innerHTML += "<button onclick='EndExam()'>End the Exam</button>";
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
        var sec = 30;
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
            test.innerHTML = "<button onclick='EndExam()'>End the Exam</button>";
            pos = 0;
            correct = 0;
            clearTimeout(tim);
            document.getElementById("endtime").innerHTML = "You Finished exam at Time is :"+min+" Minutes :" + sec+" Seconds";
            document.getElementById("starttime").style.display += 'none';
            document.getElementById("showtime").style.display += 'none';
            //document.getElementById("showtime").style.display += 'block';
            return false;

                        window.location.href = "Loginpage.htm";
                    }
                    else {
                        min = 0;
                        sec = 60;
                        document.getElementById("showtime").innerHTML = "Your Left Time is :" + min + " Minutes :" + sec + " Seconds";
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



<div id="Content">
<div id="PageHeading">
<h1><marquee direction="right" behavior="alternate">All the Best</marquee></h1>
</div>

<div id="ContentLeft">
<h2></h2><br>
<img id="online_start" src="exam.png" width="1400px;" height="200px;">
<br>
<h2>Online Examination System(OES) is a Multiple Choice Questions(MCQ) based 
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

<br></br>

<div id="showtime" ></div>
</section>
</div>

</div>


<div id="Footer">Made by - Pradipta Ghosh</div>

    
    <center style="font-size:20px;background:red"><u><a style="color:white;">Privacy Policy</a></u> <u><a style="color:white">Terms & Conditions</a></u></center>
<center style="font-size:20px;background:#17D4FE">Copyright © By Pradipta Ghosh.com 2019</center>

    
