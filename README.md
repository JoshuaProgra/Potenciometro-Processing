# Potenciometro-Processing
import processing.serial.*;

Serial puerto;

float r;
float g;
float b;

void setup() {

  fullScreen();
  //size(700, 500);
  background(255);
  
  puerto = new Serial(this, Serial.list()[2], 9600);
  puerto.bufferUntil('\n');
}
void serialEvent(Serial port) {

  String inString = port.readStringUntil('\n');
  if (inString != null) {
    float[] value = float(split(inString, '/'));
    r = value[0];
    g = value[1];
    b = value[2];
  }
}
void draw() {

  background(r, g, b);
  rectMode(CORNER);
  strokeWeight(6);
  stroke(255,212,0);
  fill(r, 0, 0);
  rect(width/4.66, height-r, 100, 300);
  fill(0, g, 0);
  rect(width/2.33, height-g, 100, 300);
  fill(0, 0, b);
  rect(width/1.55, height-b, 100, 300);
  
  fill(0);
  rectMode(CENTER);
  rect(349,192,500,40);
  rect(355,83,446,110);
  
  fill(255);
  textSize(20);
  text("INGENIERIA BIOMEDICA",231,65);
  text("AÑO 2020.....OH YEAH!!!! ",230,108);
  text(r, 160, 200);
  text(g, 310, 200);
  text(b, 460, 200);
}
