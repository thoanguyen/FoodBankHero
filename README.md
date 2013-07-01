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
			
			var timer = 10;
			
			
			var newFruitList = new Array();
			for (var i = 0; i < 9; i++)	{
				newFruitList[i] = 0;
			
			/*
				var random = (Math.ceil(Math.random ()*6))
					switch (random){
					case 1: newFruitList[i] = new Fruit (pear);
						break;
					case 2: newFruitList[i] = new Fruit (banana);
						break;
						
					case 3: newFruitList[i] = new Fruit (apple);
						break;
						
					case 4: newFruitList[i] = new Fruit (orange);
						break;

					case 5: newFruitList[i] = new Fruit (corn);
						break;
						
					case 6: newFruitList[i] = new Fruit (carrot);
						break;
				}*/
			}
			
		//context drawImage needs an image object, an x and y
			function draw(){
				context.clearRect(0, 0, theCanvas.width, theCanvas.height);
				context.drawImage(myImage,0,0,theCanvas.width,theCanvas.height);
				context.drawImage(hand,0,450, 200,150);
				context.drawImage(hand2,300,450, 200,150);
				context.drawImage(hand3,600,450, 200,150);
			
				for (var i = 0; i < 9; i++)
					if (newFruitList[i] !=0)
						newFruitList[i].dropDown(); 
				}
			myImage.onload = function(){
			}
			
		//Fruit dropping function
			function Fruit(img,x,y){
				this.init = function(){
				this.column = Math.floor(Math.random()*3);
				//if(column == 1){}
				}
				
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
				context.drawImage(img,this.xpos,this.ypos,200,200);
				};
			}
			
			function gameloop(){
				update()
				draw()
				}
			setInterval(gameloop,1000/60)
			function update(){
				timer  = timer - 1;
				//console.log(timer)
				
				for (var i = 0; i <9; i++){
				if ((newFruitList[i] == 0 && timer<0) || (newFruitList[i] !=0 && newFruitList[i].ypos > 450 && timer < 1)){
					timer = 50;
					var random = (Math.ceil(Math.random ()*6))
					switch (random){
					case 1: newFruitList[i] = new Fruit (pear, 300, 400);
						break;
					case 2: newFruitList[i] = new Fruit (banana, 300, 400);
						break;
						
					case 3: newFruitList[i] = new Fruit (apple, 300, 400);
						break;
						
					case 4: newFruitList[i] = new Fruit (orange, 300, 400);
						break;

					case 5: newFruitList[i] = new Fruit (corn, 300, 400);
						break;
						
					case 6: newFruitList[i] = new Fruit (carrot, 300, 400);
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
					for (var i = 0; i <9; i++){
						if (newFruitList[i] !=0 && newFruitList[i].xpos > -10 && newFruitList[i].xpos <100 && newFruitList[i].ypos<450 && newFruitList[i].ypos>200){
							newFruitList[i]=0;
						}
					}
					break;
				
				case 83: console.log("pressS");
					for (var i = 0; i <9; i++){
						if (newFruitList[i] !=0 && newFruitList[i].xpos >= 100 && newFruitList[i].xpos <550 && newFruitList[i].ypos<450 && newFruitList[i].ypos>200){
							newFruitList[i]=0;
					}
					}
					break;
						
				case 68: console.log("pressD");
					for (var i = 0; i <9; i++){
						if (newFruitList[i] !=0 && newFruitList[i].xpos >= 400 && newFruitList[i].xpos < 900 && newFruitList[i].ypos<450 && newFruitList[i].ypos>200){
							newFruitList[i]=0;
					break;
					} 
					}

			}
		}
		
		

		</script>
	</body>
</html>
								
								
								
								
			
