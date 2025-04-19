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

    int amplitude = 100;   // Height of bounce
    int frequency = 1;     // Controls bounce frequency
    int baseY = 400;       // Ground level (y position)

    initgraph(&gd, &gm, "C:\\Turboc3\\BGI");

    int screenWidth = getmaxx();

    x = 0;
    while (!kbhit()) {  // Run continuously until a key is pressed
        cleardevice();

        // Draw ground
        line(0, baseY, screenWidth, baseY);

        // Calculate bouncing y using sine function
        angle = (float)x * frequency * (PI / 180); // Convert degrees to radians
        y = baseY - (int)(amplitude * fabs(sin(angle))); // Ball stays above ground

        // Draw the ball
        setcolor(WHITE);
        setfillstyle(SOLID_FILL, RED);
        fillellipse(x, y, 15, 15); // (x, y, radiusX, radiusY)

        delay(20);

        x += 5;
        if (x > screenWidth) {
            x = 0; // Wrap back to left
        }
    }

    closegraph();
    return 0;
}

