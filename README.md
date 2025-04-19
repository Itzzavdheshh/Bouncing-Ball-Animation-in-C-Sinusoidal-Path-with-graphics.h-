# Bouncing-Ball-Animation-in-C-Sinusoidal-Path-with-graphics.h-
#include <graphics.h>

#include <conio.h>

#include <math.h>

#include <dos.h>

#define PI 3.14159265

int main()
{
   
    int gd = DETECT, gm;
    int x, y;
    float angle = 0;

    int amplitude = 100;   
    int frequency = 1;     
    int baseY = 400;       

    initgraph(&gd, &gm, "C:\\Turboc3\\BGI");

    int screenWidth = getmaxx();

    x = 0;
    while (!kbhit()) {  
        cleardevice();

        
        line(0, baseY, screenWidth, baseY);

        
        angle = (float)x * frequency * (PI / 180); 
        y = baseY - (int)(amplitude * fabs(sin(angle))); 

        
        setcolor(WHITE);
        setfillstyle(SOLID_FILL, RED);
        fillellipse(x, y, 15, 15); 

        delay(20);

        x += 5;
        if (x > screenWidth) {
            x = 0; 
        }
    }

    closegraph();
    return 0;
}

