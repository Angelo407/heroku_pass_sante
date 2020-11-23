Edit me later
url:https://www.freecodecamp.org/news/how-to-deploy-your-site-using-express-and-heroku/

1) echo "Edit me later" > README.md

2) git init

3) heroku login -i

4) heroku create passsante

5) npm init -y

6) npm install express --save

7) touch app.js
=> 
    // create an express app
    const express = require("express")
    const app = express()

    // use the express-static middleware
    app.use(express.static("public"))

    // define the first route
    app.get("/", function (req, res) {
      res.send("<h1>Hello World!</h1>")
    })

    // start the server listening for requests
    app.listen(process.env.PORT || 3000, 
      () => console.log("Server is running..."));

8) mkdir public
cd public

9) touch index.html styles.css script.js

    html:
    <!DOCTYPE html>
    <head>
      <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
      <link href="https://fonts.googleapis.com/css?family=Alegreya|Source+Sans+Pro&display=swap" rel="stylesheet">
      <link rel="stylesheet" type="text/css" href="styles.css">
    </head>
    <html>
    <body>
    <h1>Lorem Ipsum generator</h1>
      <p>How many paragraphs do you want to generate?</p>
      <input type="number" id="quantity" min="1" max="20" value="1">
      <button id="generate">Generate</button>
      <button id="copy">Copy!</button>
    <div id="lorem">
    </div>
    <script type="text/javascript" src="script.js"></script>
    </body>
    </html>

    style:
    h1 {
      font-family: 'Alegreya' ;
    }
    body {
      font-family: 'Source Sans Pro' ;
      width: 50%;
      margin-left: 25%;
      text-align: justify;
      line-height: 1.7;
      font-size: 18px;
    }
    input {
      font-size: 18px;
      text-align: center;
    }
    button {
      font-size: 18px;
      color: #fff;
    }
    #generate {
      background-color: #09f;
    }
    #copy {
      background-color: #0c6;
    }

    javascript:
    $("#generate").click(function(){
      var lorem = $("#lorem");
      lorem.html("");
      var quantity = $("#quantity")[0].valueAsNumber;
      var data = ["Lorem ipsum", "quia dolor sit", "amet", "consectetur"];
      for(var i = 0; i < quantity; i++){
        lorem.append("<p>"+data[i]+"</p>");
      }
    })

    $("#copy").click(function() {
      var range = document.createRange();
      range.selectNode($("#lorem")[0]);
      window.getSelection().removeAllRanges();
      window.getSelection().addRange(range);
      document.execCommand("copy");
      window.getSelection().removeAllRanges();
      }
    )

10) echo "web: node app.js" > Procfile