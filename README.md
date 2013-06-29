FoodBankHero
============
<!DOCTYPE html>
<html>
  <head>
	</head>
	<body>
		<canvas id="myCanvas" width="1000" height="600" style="border: 3px solid #000000;">
		</canvas>
		<script type = "text/javascript">

			var theCanvas = document.getElementById("myCanvas");
			var context = theCanvas.getContext ("2d");
			document.addEventListener("keydown", buttonPress, false);
			var myImage = new Image ();
			myImage.src = "background.jpg";
			var fruitSourceList = new Array("apple.jpg","banana.jpg","pear.jpg","orange.jpg","carrot.jpg","corn.jpg");
			var fruitNameList = new Array("apple","banana","pear","orange","carrot","corn");

			var pear = new Image ();
			pear.src = "pear.jpg";
			var apple = new Image();
			apple.src = "apple.jpg";
			var banana = new Image ();
			banana.src = "banana.jpg";
			var hand = new Image ();
			hand.src = "hand.png";
			var hand2 = new Image ();
			hand2.src = "hand.png";
			var hand3 = new Image ();
			hand3.src = "hand.png";
			
			//context drawImage needs an image object, an x and y
			myImage.onload = function(){
								
						}
				
						function Fruit(img,x,y){
								this.img;
								this.myImage;
								
								this.init = function(){
									this.column = Math.floor(Math.random()*3);
										if(column == 1){}
										
									this.myImage = new Image();
									//myImage.src = 
								}
								this.xpos = x;
								this.ypos = y +Math.random(100)-200;
								
								this.vel = Math.random(1)+ 3;
								
								this.dropDown = function(){
								
										this.ypos += this.vel;
										//alert(this.ypos);
										context.drawImage(img,this.xpos,this.ypos,200,200);
								};
						}
						
						var fruit1 = new Fruit(pear, 10, 0);
						var fruit2 = new Fruit(banana, 300, -15);
						var fruit3 = new Fruit(apple, 600, 15);
						function gameloop(){
								update()
								draw()
								}
						setInterval(gameloop,1000/60)
						function update(){
							
						}
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
						
						function buttonPress (Evt){
							console.log(Evt.keyCode); 
							var n;
						//buttons for catcher: a=65, s=83, d=67;
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
								
								
								
								
			
