# myConvexHull.py

My convex script generally works by using the command:

```
python -i myConvexHull.py -print <Y or N> -save <Y or N> -conf <Y or N> -plot <Y or N>
```

```<-print>``` - Choose if you want to print the convex points to the console. Y for print, N for don't print.

```<-save>``` - Choose if you want to save the convex points. Y for save, N for don't save.

```<-conf>``` - If Y, the script will confirm that no points lie outside the convex, if it does, it will let you know. N is used to not do the check.

```<-plot>``` - Specify if you want to plot your coordinates, with the convex points highlighted. Default is Y (yes).

How the script fundamentally works is that it takes your coordinates (inserted in ```coord = []``` with shape of ```coord = [[x1,y1],[x2,y2],[x3,y3],...,[xn,yn]]```) and sorts your coordinates from the points with the lowest x-value to the highest x-value. The algorithm starts by using the lowest point, let's call it p0, and gives it an angle 90. This angle is then reset using:
90 - 90 + 360

The algorithmn then calculates the angle (<theta;>)between p0 and every other point in the data and takes those owns and alters them with equation:

angle - 90 + 360.
If the angle is bigger than 360, then 360 is just subtracted from it.

Whichever altered angle is the greatest is then chosen as the new target point, let's call it p1. The unaltered angle between p0 and p1 is then reset to 360. The angle between p1 and every other point is then calculated, with these angles altered using:

angle - p1_ang + 360
with any altered angle greater than 360 having 360 subtracted from it.

The coordinate which has the greatest altered angle with p1 is then chosen as the new target angle and the process continues. The algorithm ends when the angle between pn and p0 is the greatest angle again.

