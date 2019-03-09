// Declare Mover object
Mover mover, mover2, mover3, mover4;
PVector co1, co2;
int a = 1;
int b = 1;
int c = 1;
int d = 1;


void setup() {
  size(displayWidth, 755);
  smooth();
  background(0);
  // Make Mover object
  mover = new Mover(); 
  mover2 = new Mover();
  mover3 = new Mover();
  mover4 = new Mover();

}

void draw() {
  noStroke();
  fill(0, 10);
  rect(0, 0, width, height);
  
  // Call functions on Mover object.
  if (a < 2)
  {
    mover.set_location(new PVector(random(0, 1000), 0));
   a++;
  }
  mover.update();
  mover.checkEdges();
  mover.display(); 
  mover.ApplyFriction();
  
  
  if (b < 2)
  {
  mover2.set_location(new PVector(random(0, 1000), 0));
  b++;
  }
  mover2.update();
  mover2.checkEdges();
  mover2.display(); 
  mover2.ApplyFriction();

  
  if (c < 2)
  {
  mover3.set_location(new PVector(random(0, 1000), 0));
  c++;
  }
  mover3.update();
  mover3.checkEdges();
  mover3.display(); 
  mover3.ApplyFriction();
  
  if (d < 2)
  {
  mover4.set_location(new PVector(random(0, 1000), 0));
  d++;
  }
  mover4.update();
  mover4.checkEdges();
  mover4.display(); 
  mover4.ApplyFriction();
  
  
  //how to do this more efficiently?
  mover.CheckCollision(mover, mover2);
  mover.CheckCollision(mover, mover3);
  mover.CheckCollision(mover, mover4);

  mover.CheckCollision(mover2, mover3);
  mover.CheckCollision(mover2, mover4);

  mover.CheckCollision(mover3, mover4);

}

class Mover {

  PVector location;
  PVector velocity;
  PVector acceleration;
  PVector friction;
  float topspeed;

  Mover() {
    location = new PVector(8, 8);    
    velocity = new PVector(random(5.0),0);
    acceleration = new PVector(0, random(0.8));  //x, y values
    friction = new PVector(0.0001, 0.001);
    topspeed = 30;
  }
  
  void set_location(PVector a){
    location.add(a);
  }

  void update() {
    // Velocity change by acceleration and is limited by topspeed.
      velocity.add(acceleration);
  
    if (velocity.x <= 0){
    acceleration.x = acceleration.x * -1;
    } //so that it goes left and right freely
    velocity.limit(topspeed);
    location.add(velocity);
  }
  
   void display() {
    noStroke();
    fill(255);
    ellipse(location.x,location.y,16,16);
  }

  void checkEdges() {

    if (location.x >= width - 8 || location.x <= 8){
       if (location.x >= width - 8){
      location.x = width -8;
      }
      else if ( location.x <= 8) {
        location.x = 8;
      }
      velocity.x = velocity.x * -1;
    }
       
    if (location.y >= height - 8 || location.y <= 8){
      if (location.y >= height - 8){
      location.y = height -8;
      }
      else if ( location.y <= 8) {
        location.y = 8;
      }
      velocity.y = velocity.y * -1;
    }
  }
    
    
  void ApplyFriction() {
      
      if (abs(velocity.x) != 0 && abs(velocity.y) != 0){
        if (velocity.x > 0 && velocity.y > 0){
            velocity.sub(friction);
        }
        else if (velocity.x > 0 && velocity.y < 0){
            velocity.x = velocity.x - friction.x;
            velocity.y = velocity.y + friction.y;
        }
        else if (velocity.x < 0 && velocity.y < 0){
            velocity.add(friction);
        }
        else if (velocity.x < 0 && velocity.y > 0){
            velocity.x = velocity.x + friction.x;
            velocity.y = velocity.y - friction.y;
        }
      }
  }
 
 void CheckCollision(Mover mover1, Mover mover2){
  if (PVector.dist(mover1.location, mover2.location) <= 16)
  {
    //calculate degrees
    co1 = new PVector(mover2.location.x - mover1.location.x, mover2.location.y - mover2.location.y);
    float a = PVector.angleBetween(mover1.location, co1); //in radian
    float b = PVector.angleBetween(mover2.location, co1);
    
    if (a > PI/2) 
    {
      a = PI - a;
    }
    else if (b > PI/2)
    {
      b = PI - b;
    }
    
    //rotate
    mover1.velocity.rotate(abs(PI - a));
    mover2.velocity.rotate(abs(PI - b));
 }
  
}
}
