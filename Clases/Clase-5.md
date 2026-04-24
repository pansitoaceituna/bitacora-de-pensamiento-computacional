let tinte = 360
let = tinteComplementario = 0
let diametro = 100
function setup() {
  createCanvas(500, 500);
  colorMode(HSB,360,100,100)
  
  frameRate(20)
}

function draw() {
  if(tinte > 180)
  tinteComplementario = tinte - 180
  
  if(tinte < 180)
  tinteComplementario = tinte + 180
  
    
  
diametro = (mouseX + mouseY) /2
 
    tinte = tinte - 5
  
  if(tinte < 0){
    
  tinte = 360}
  
  
  background(tinteComplementario,100,100);
  
  //noFill(tinte,40,100)
  //ellipse(width/2, height/2, diametro, diametro)
    // Style the arc.
  
  noStroke();
  fill(tinte, 40, 100);

  let biteSize = PI / 16;
  let startAngle = biteSize * sin(frameCount * 0.1) + biteSize;
  let endAngle = TWO_PI - startAngle;

  arc(width/2, height/2, diametro, diametro, startAngle, endAngle, PIE);
  
  
  push()
  
  beginShape()
  
  vertex (width * 3/4, height/2)
  
  vertex(width*3/4, height/3)
  
  vertex(width*2/3, height/3)
  
  endShape()
  
  pop()
  
   
  push()
  
  beginShape()
  
  vertex (width * 3/4, height*2/3)
  
  vertex(width*3/4, height/3)
  
  vertex(width*2/3, height/3)
  
  endShape()
  
  pop()
  
  
  
  fill(0, 0, 0)
  textSize(20)
  textAlign(CENTER,CENTER)
  text("no me muevas \n" + tinte, width /2, height/2)
  textFont('Courier New')
}
