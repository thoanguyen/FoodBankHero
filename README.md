<!DOCTYPE html>
<html>
	<head>
	</head>
	<body>
		<canvas id="myCanvas" width="900" height="600" style="border: 3px solid #000000; z-index:0; position:absolute;" >
		</canvas>
		<canvas id="healthCanvas" width="200" height="100" style="z-index:1; position: absolute;">
		</canvas>
		<script type = "text/javascript">
		
		//Background	
			var theCanvas = document.getElementById("myCanvas");
			var context = theCanvas.getContext ("2d");
			var myImage = new Image ();
			myImage.src = "Background.png";
			
		//Images
			var pear = new Image ();
			pear.src = "pear.png";
			var apple = new Image();
			apple.src = "apple.png";
			var banana = new Image ();
			banana.src = "banana.png";
			var carrot = new Image();
			carrot.src = "carrot.png";
			var corn = new Image ();
			corn.src = "corn.png";
			var orange = new Image ();
			orange.src = "orange.png";
			var hand = new Image ();
			hand.src = "newHand.png";
			var hand2 = new Image ();
			hand2.src = "newHand.png";
			var hand3 = new Image ();
			hand3.src = "newHand.png";
			var Background3 = new Image ();
			Background3.src = "Background3.png";
			var donut = new Image ();
			donut.src = "donut.png";
			var icecream = new Image ();
			icecream.src = "icecream.png";
			var pizza = new Image ();
			pizza.src = "pizza.png";
			var cookie = new Image ();
			cookie.src = "cookie.png";
			var Chickenleg = new Image ();
			Chickenleg.src = "Chickenleg.png";
			var frenchfries = new Image ();
			frenchfries.src = "frenchfries.png";
			

			var handani = new Image ();
			handani.src = "hands.png";
				
			var GameStart = true;
			var GameOn = false;
			
			var timer = 10;
			var points = 0;
			var newFruitList = new Array();
			for (var i = 0; i < 9; i++)	{
				newFruitList[i] = 0;
				}

			myCanvas.addEventListener("mousedown", function() {
				GameStart = false;
				GameOn =  true;
				},false);
		
		//Health Bar
			function getHexString(numX){
				var hexStr = numX.toString(16); //16 makes toString display as hex
				if(hexStr.length == 1) hexStr = '0' + hexStr;
					if(hexStr.length != 2) alert("Number outside conversion range (0 to 255):" + numX);
				return hexStr;
			}

		//context drawImage needs an image object, an x and y
			function draw(){
				if(GameStart) {
					context.drawImage(Background3, 0, 0, 900,600)
				}
				else if (GameOn){
					
					context.drawImage(myImage,0,0,theCanvas.width,theCanvas.height);
					newHands[0].draw();
					newHands[1].draw();
					newHands[2].draw();
					for (var i = 0; i < 9; i++)
						if (newFruitList[i] !=0)
						newFruitList[i].dropDown();
						
		//point system part a
				context.fillStyle = "rgb(0, 0, 0)"; //"#000000"
				context.font = "30px Consolas";
				context.fillText ("POINTS: " + points, 30,
				40);
				context.strokeRect(30,45,300,20);
				
				if (points >30)
				{
					context.fillStyle="#00" + getHexString((Math.floor(30*255/30))%255) + "00";
					context.fillRect(30,45,30*10,20);
				}
				else
				{
					context.fillStyle="#00" + getHexString((Math.floor(points*255/30))%255) + "00";
					context.fillRect(30,45,points*10,20);
				}
					}
				}	
				
				
				myImage.onload = function(){
				}
			

			//Fruit dropping function
				function Fruit(img,x,y, points){
				this.init = function(){
				this.column = Math.floor(Math.random()*3);
				}
				this.score = points;	
					
				//this.xpos = Math.random()*900;
				var random = (Math.ceil(Math.random ()*3))
				switch (random){
				case 0: this.xpos = 0;
				case 1: this.xpos = 0;
					break;
				case 2: this.xpos = 300;
					break;
				case 3: this.xpos = 600;
					break;
				}
			
				this.ypos = Math.random(100)-200;
				this.vel = Math.random(1)+ 3;
				this.dropDown = function(){
				this.ypos += this.vel;
				context.drawImage(img,this.xpos,this.ypos,175,175);
				}
			}
				
			function glove(avi, x, y){
				this.pic = avi;
				this.xpos = x;
				this.ypos = y;
				this.xclip = 0;
				this.frameCount = 1;
				this.aniFlag = false;
				
				this.draw = function() {
				if (this.aniFlag == false)
					context.drawImage(this.pic, 0, 0, 178, 300, this.xpos, this.ypos, 200, 150);
				else {
					context.drawImage(this.pic, this.xclip, 0, 178, 300, this.xpos, this.ypos, 200, 150);
					this.xclip = this.xclip + 180;
					this.frameCount = this.frameCount + 1;
					if (this.frameCount > 10)
					{
						this.aniFlag = false;
						this.xclip = 0;
						this.frameCount = 1;
					}
				}
						
				};
			}
			
			var newHands = new Array();
			newHands[0] = new glove (handani, 0, 450);
			newHands[1] = new glove (handani, 300, 450);
			newHands[2] = new glove (handani, 600, 450);
		
	
		//Gameloop
			function gameloop(){
				update()
				draw()
				}
			setInterval(gameloop,1000/60)
			
			function update(){
			
				timer  = timer - 1;
				
				
				//console.log(timer)a
				
				for (var i = 0; i <9; i++){
				if ((newFruitList[i] == 0 && timer<0) || (newFruitList[i] !=0 && newFruitList[i].ypos > 450 && timer < 1)){
					timer = 50;
					var random = (Math.ceil(Math.random ()*12))
					switch (random){
					case 1: newFruitList[i] = new Fruit (pear, 300, 400, 5);
						break;
					case 2: newFruitList[i] = new Fruit (banana, 300, 400, 12);
						break;
						
					case 3: newFruitList[i] = new Fruit (apple, 300, 400, 10);
						break;
						
					case 4: newFruitList[i] = new Fruit (orange, 300, 400, 7);
						break;

					case 5: newFruitList[i] = new Fruit (corn, 300, 400, 3);
						break;
						
					case 6: newFruitList[i] = new Fruit (carrot, 300, 400, 10);
						break;
					case 7: newFruitList[i] = new Fruit (donut, 300, 400, -5);
						break;						
					case 8: newFruitList[i] = new Fruit (pizza, 300, 400, -7);
						break;
					case 9: newFruitList[i] = new Fruit (chickenleg, 300, 400, -10);
						break;
					case 10: newFruitList[i] = new Fruit (cookie, 300, 400, -3);
						break;
					case 11: newFruitList[i] = new Fruit (icecream, 300, 400, -5);
						break;
					case 12: newFruitList[i] = new Fruit (frenchfries, 300, 400, -3);
						break;
						}	
					}	
				}			
			}
			
			
		//buttons for catcher: a=65, s=83, d=67;
			document.addEventListener("keydown", buttonPress, false);

			function buttonPress (Evt){
				console.log(Evt.keyCode); 
				//var n;
				switch (Evt.keyCode){
				case 65: console.log("pressA");
					newHands[0].aniFlag = true;
					for (var i = 0; i <9; i++){
						if (newFruitList[i] !=0 && 
						newFruitList[i].xpos > -10 && 
						newFruitList[i].xpos <100 && 
						newFruitList[i].ypos<450 && 
						newFruitList[i].ypos>200){
						points = points + newFruitList[i].score;
						if (points < 0) points = 0;
						newFruitList[i] = 0;
						}
					}
					break;
				
				case 83: console.log("pressS");
					newHands[1].aniFlag = true;
					for (var i = 0; i <9; i++){
						if (newFruitList[i] !=0 && 
						newFruitList[i].xpos >= 100 &&
						newFruitList[i].xpos <550 && 
						newFruitList[i].ypos<450 &&
						newFruitList[i].ypos>200){
						points = points + newFruitList[i].score;
						if (points < 0) points = 0;

						newFruitList[i] = 0;
						}
					}
					break;
						
				case 68: console.log("pressD");
					newHands[2].aniFlag = true;
					for (var i = 0; i <9; i++){
						if (newFruitList[i] !=0 && 
						newFruitList[i].xpos >= 400 && 
						newFruitList[i].xpos < 900 && 
						newFruitList[i].ypos<450 && 
						newFruitList[i].ypos>200){
						points = points + newFruitList[i].score;
						if (points < 0) points = 0;

						newFruitList[i] = 0;
					
					break;
						} 
					}
					
		//The hand animation 
			function draw(){
				context.clearRect (0,0,myCanvas.width, myCanvas.height)
				
				sheet = "hands2.png";
				height = 200; 
				width = 150;
				row = 1;
				frames = 10;
						
				rowCount = 1;
				frameCount = 1;
				xMarker = 78.9;
				yMark = 214;
				xpos = x;
				ypos = y;
			
			context.drawImage(image, cx, cy, width, height, x, y, scalex, scaley);
				div.style.backgroundPosition = (-xpos+"20px"); 
				}	
			draw = function () {
				context.drawImage( hands2.png, 0, 214, 200, 150, 0, 450, 78.9, 200);
				rowCount += 1;
				frameCount += 1;
				xMarker += 78.9;
				}
				if (rowCount > row){
					rowCount = 1;
					xMarker = 0;
					yMarker += 200;
					}
				
				if (rowCount > frames){
					xMarker = 0;
					yMarker = 0;
					rwoCount = 1;
					frameCount = 1;
					}					

				image.onload = function(){
					setInterval(loop, 1000 / 30);
					xpos += frameSize;
					index+=1;
					}
					if (index >= numFrames){
						xpos= 0
						ypos= 450
						index= 0
						} 
		
				animation.onload = function (){
					width: 200;
					height: 150;
					background.image = (hands.png);
					}
				}
			}
		
		</script>
	</body>
</html>
								
								
								
								
			
