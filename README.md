# Rastercaster
## Quade Curry

### Sunset square

![Sunset square](http://45.79.151.170/1.png)
```
vec3 color;
float x = gl_FragCoord.x;
float y = gl_FragCoord.y;
float mx = mouse.x;
float my = dimensions.y - mouse.y;

// Each if statement here draws a square around the mouse, in pre-defined colors.
if (x >= mx - 1000.0 && x <= mx + 1000.0) {
  if (y >= my - 1000.0 && y <= my + 1000.0) {
    color = vec3(0.0, 0, 0.1);
  }
}
if (x >= mx - 900.0 && x <= mx + 900.0) {
  if (y >= my - 900.0 && y <= my + 900.0) {
    color = vec3(0.0, 0, 0.2);
  }
}
if (x >= mx - 800.0 && x <= mx + 800.0) {
  if (y >= my - 800.0 && y <= my + 800.0) {
    color = vec3(0.0, 0, 0.25);
  }
}
if (x >= mx - 700.0 && x <= mx + 700.0) {
  if (y >= my - 700.0 && y <= my + 700.0) {
    color = vec3(0.1, 0, 0.25);
  }
}
if (x >= mx - 600.0 && x <= mx + 600.0) {
  if (y >= my - 600.0 && y <= my + 600.0) {
    color = vec3(0.2, 0, 0.25);
  }
}
if (x >= mx - 500.0 && x <= mx + 500.0) {
  if (y >= my - 500.0 && y <= my + 500.0) {
    color = vec3(0.3, 0, 0.25);
  }
}
if (x >= mx - 400.0 && x <= mx + 400.0) {
  if (y >= my - 400.0 && y <= my + 400.0) {
    color = vec3(0.4, 0, 0.25);
  }
}
if (x >= mx - 300.0 && x <= mx + 300.0) {
  if (y >= my - 300.0 && y <= my + 300.0) {
    color = vec3(0.5, 0, 0.25);
  }
}
if (x >= mx - 200.0 && x <= mx + 200.0) {
  if (y >= my - 200.0 && y <= my + 200.0) {
    color = vec3(0.75, 0, 0.25);
  }
}
if (x >= mx - 100.0 && x <= mx + 100.0) {
  if (y >= my - 100.0 && y <= my + 100.0) {
    color = vec3(1, 0, 0);
  }
}
```

### Cool fade
#### I need to make this my screensaver.
![Cool fade](http://45.79.151.170/2.png)
```
vec3 color;
float x = gl_FragCoord.x / dimensions.x;
float y = gl_FragCoord.y / dimensions.y;
float r = abs(sin((3.14159 / 180.0) * time));
float g = abs(sin((3.14159 / 180.0) * (time + 20.0)));
float b = abs(sin((3.14159 / 180.0) * (time + 40.0)));
color = vec3(r * x, g * y, b);
```

### Boring quad
#### -- with seizure warning
![Boring quad](http://45.79.151.170/3.png)

```
vec3 color;
float x = gl_FragCoord.x;
float y = gl_FragCoord.y;
float mx = mouse.x;
float my = dimensions.y - mouse.y;

float offx = mx / dimensions.x;
float offy = my / dimensions.y;

if (mod(mx, 2.0) == 0.0) {
  discard;
}

if (x < mx && y < my) {
  color = vec3(offx, offy, offx / 2.0);
} else if (x < mx && y > my) {
  color = vec3(offx / 2.0, offx, offy);
} else if (x > mx && y > my) {
  color = vec3(offy, offx / 2.0, offx);
} else if (x > mx && y < my){
  color = vec3(offy, offx, offy / 2.0);
}
```

### Sine spiral
#### This actually ended up cooler than I thought. Initially I was just seeing if I could draw a sine wave across the screen, but I stopped when this happened.

![Sine spiral](http://45.79.151.170/4.png)
```
vec3 color;
float x = gl_FragCoord.x;
float y = gl_FragCoord.y;
float px;
float py;
float size = 25.0;
float number = 100.0;

for (float i = 0.0; i < number; i += 1.0) {
  // Vary the x-value of the point by the current iteration of the for loop, then use dimensions.x to scale the points to fit the horizontal screen space.
  px = i * (dimensions.x / number);
  // Use sin() to get a y-value based on the time, and then use dimensions.y to make it fit the vertical screen space.
  py = abs(sin(time - i)) * dimensions.y;

  // Draw a point with an adjustable size
  if ((x >= px - (size / 2.0) && (x <= px + (size / 2.0))) && (y >= py - (size / 2.0) && (y <= py + (size / 2.0)))) {
    color = vec3(py / dimensions.y, sin(time) * (i / number), sin(time) + 1.25);
  }
}
```

### Sine W A V E

![Sine W A V E](http://45.79.151.170/5.png)
```
vec3 color;
float x = gl_FragCoord.x;
float y = gl_FragCoord.y;
float px;
float py;
float size = 20.0;
float number = 200.0;

for (float i = 0.0; i < number; i += 1.0) {
  px = i * (dimensions.x / number);
  py = abs(sin(time - i)) * (dimensions.y / i * 20.0);
  size = size + mod(size + i, 4.0);

  if ((x >= px - (size / 2.0) && (x <= px + (size / 2.0))) && (y >= py - (size / 2.0) && (y <= py + (size / 2.0)))) {
    color = vec3(py / dimensions.y, sin(time) * (i / number), sin(time) + 1.25);
  }
}
```
