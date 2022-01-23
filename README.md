# Web Page for Paint Application

## AIM:

To design a static website for Paint Application using HTML5 canvas.

## DESIGN STEPS:

### Step 1:

Requirement collection.

### Step 2:

Creating the layout using HTML,CSS and canvas.

### Step 3:

Write javascript to capture move events.

### Step 4:

Perform the drawing operation based on the user input.

### Step 5:

Validate the layout in various browsers.

### Step 6:

Validate the HTML code.

### Step 6:

Publish the website in the given URL.

## PROGRAM :
~~~

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Paint Application</title>
    <link rel="icon" href="./img/logo.png" type="image/x-icon" />
    <style>
         .text{
            text-align: center;
            padding-top:20px;
            padding-bottom: 10px;
            font-size: 80px;
            color: rgb(255, 255, 255);
            font-family: 'Times New Roman', Times, serif;
        }
        #content{
            padding-left: 740px;
            padding-top: 30px;
           
        }
        #myCanvas{
          background-color: #ffdadd;
          box-shadow: inset 0 0 5px #b6b6b6; 
          backdrop-filter: blur(15px);
          border-radius: 2px;
          border: 5px solid #332525;
        }
        #buttonstyle{
          background-color: #9b9b9b;
          border: 4px solid #ffffff;
          border-radius: 8px;
          color: black;
          padding: 20px 30px;
          text-align: center;
          display: inline-block;
          font-size: 20px;
          margin: 4px 2px;
          cursor: pointer;
        }
        #buttonstyle:hover{
            background-color:#ffffff36;
            transition: 0.5s;
        }
        #background{
            background-image: url(./img/cs.jpg);
        }
        #shooky{
            border: 2px solid #ffffff;
            border-radius: 25px;
            padding: 25px 25px;
            text-align: center;
            display: inline-block;
            font-size: 16px;
            margin: 4px 2px;
            cursor: pointer;
        }
        #shooky:hover{
            opacity: 20%;
            transition: 0.21s;
        }
        .footer {
            display:block;
            font-size: 60px;
            font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
            margin: 0px 0px 0px 0px;
            padding-top: 10px;
            color: #ffffff;
        }
        </style>
  </head>
  <body id="background">
    <div class="text">CANVAS</div>
    <div id="content">
      <canvas id="myCanvas" width="800" height="850" onclick="showCoords(event)"></canvas></div>
      <center>
      <button onclick="shape=1" id="buttonstyle" >Solid Circle</button>
      <button onclick="shape=2" id="buttonstyle">circle</button>
      <button onclick="shape=3" id="buttonstyle">Solid Square</button>
      <button onclick="shape=4" id="buttonstyle">Square</button>
      <button onclick="shape=5" id="buttonstyle">Solid Triangle</button>
      <button onclick="shape=6" id="buttonstyle">Triangle</button>
      <br>
      <button onclick="size()" id="buttonstyle" >Change size</button></center>
      <center>
      <button onclick="change_color(this)" id="shooky" style="background: white;"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(255, 72, 72);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(255, 115, 1);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(252, 255, 60);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(94, 255, 45);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(7, 184, 1);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(49, 231, 255);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(46, 112, 255);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(213, 76, 255);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(153, 0, 255);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(54, 0, 124);"></button>
      <button onclick="change_color(this)" id="shooky" style="background: rgb(0, 0, 0);"></button>
      </center>

      <script>


        const canvas = document.getElementById("myCanvas");
        const ctx = canvas.getContext("2d");
        ctx.fillStyle = "#FF0000";
        canvas.height = canvas.width;
        ctx.transform(1, 0, 0, -1, 0, canvas.height);
        let xMax = canvas.height;
        let yMax = canvas.width;
        let csize= 20;
        let sqsize= 50;
        let tsize=50;
        let tata="black";
        function size(){   
          if (shape==1 ||shape==2){
            let c= prompt("Please enter size of circle", "ex:100,50");
            csize=c;
          } 
          if (shape==3 ||shape==4){
            let s = prompt("Please enter size of square", "ex:100,20");
            sqsize=s;
          }
          if (shape==5 || shape==6){
            let t= prompt("Please enter size of triangle","ex:50,84");
            tsize=t;
          }
        }
        function change_color(element){
          tata=element.style.background;
        }
        function showCoords(event)
        {
          var x = event.clientX-545;
          var y = yMax-event.clientY;
          var coords = "X coords: " + x + ", Y coords: " + y;
          document.getElementById("demo").innerHTML = coords;
    
          if (shape==1){
            ctx.beginPath();
            ctx.arc(x, y, csize, 0, 2 * Math.PI);
            ctx.fillStyle=tata;
            ctx.fill();
          }
          if (shape==2){
            ctx.beginPath();
            ctx.arc(x, y, csize, 0, 2 * Math.PI);
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==3){
            ctx.beginPath();
            ctx.rect(x-(sqsize/2),y-(sqsize/2), sqsize,sqsize);
            ctx.fillStyle=tata;
            ctx.fill();
          }
          if (shape==4){
            ctx.beginPath();
            ctx.rect(x-(sqsize/2),y-(sqsize/2), sqsize,sqsize);
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==6){
            ctx.beginPath();
            ctx.moveTo(x, y);
            ctx.lineTo(x-(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x+(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x,y)
            ctx.strokeStyle=tata;
            ctx.stroke();
          }
          if (shape==5){
            ctx.beginPath();
            ctx.moveTo(x, y);
            ctx.lineTo(x-(tsize/2),y-(tsize*0.86602));
            ctx.lineTo(x+(tsize/2),y-(tsize*0.86602));
            ctx.fillStyle=tata;
            ctx.fill();
          }    
        }
      </script>
    <center><p id="demo" style="color: white;"></p></center>
    <div class="footer"><center>Developed by Vineesh.M</center></div>
  </body>
</html>
~~~


## OUTPUT:

### Before:
![Screenshot (82)](https://user-images.githubusercontent.com/93427254/150687127-50494d73-5084-4cef-811e-3ab66046fbb5.png)

### After:
![Screenshot (81)](https://user-images.githubusercontent.com/93427254/150687131-8be3448d-5f6e-46ef-9aba-fe0a1bd3b2c2.png)

## Result:

Thus a website is designed and validated for paint application using HTML5 canvas.
