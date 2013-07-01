<!DOCTYPE html>
<html>
	<head>
	</head>
	<body>
		<canvas id="myCanvas" width="900" height="600" style="border: 3px solid #000000;">
		</canvas>
		<script type = "text/javascript">
		
		//Background	
			var theCanvas = document.getElementById("myCanvas");
			var context = theCanvas.getContext ("2d");
			var myImage = new Image ();
			myImage.src = "abstract.jpg";
			
		//Images
			var pear = new Image ();
			pear.src = "pear.png";
			var apple = new Image();
			apple.src = "apple.png";
			var banana = new Image ();
			banana.src = "banana.png";
			var hand = new Image ();
			hand.src = "newHand.png";
			var hand2 = new Image ();
			hand2.src = "newHand.png";
			var hand3 = new Image ();
			hand3.src = "newHand.png";
			var fruit1 = new Fruit(pear, -100, 0);
			var fruit2 = new Fruit(banana, 200, -15);
			var fruit3 = new Fruit(apple, 500, 15);
						
			
		//context drawImage needs an image object, an x and y
			function draw(){
				context.clearRect(0, 0, theCanvas.width, theCanvas.height);
				context.drawImage(myImage,0,0,theCanvas.width,theCanvas.height);
				context.drawImage(hand,0,450, 200,150);
				context.drawImage(hand2,300,450, 200,150);
				context.drawImage(hand3,600,450, 200,150);
				fruit1.dropDown();
				fruit2.dropDown();
				fruit3.dropDown();
				}
			myImage.onload = function(){
			}
			
		//Fruit dropping function
			function Fruit(img,x,y){
				this.init = function(){
				this.column = Math.floor(Math.random()*3);
				//if(column == 1){}
				}
				this.xpos = x;
				this.ypos = Math.random(100)-200;
				this.vel = Math.random(1)+ 3;
				this.dropDown = function(){
				this.ypos += this.vel;
				context.drawImage(img,this.xpos,this.ypos,500,500);
				};
			}
			
			function gameloop(){
				update()
				draw()
				}
			setInterval(gameloop,1000/60)
			function update(){
			}					
						
		//buttons for catcher: a=65, s=83, d=67;
		//document.addEventListener("keydown", buttonPress, false);

		function buttonPress (Evt){
			console.log(Evt.keyCode); 
			//var n;

			switch (Evt.keyCode){
		case 65: console.log("pressA");
			break;
	
		case 83: console.log("pressS");
			break;
			
		case 67: console.log("pressD");
			break;
			} 
		}
		
		
		
		
		</script>
	</body>
</html>
								
								
								
								
									
								
								
			
