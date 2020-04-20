# python3d
Python library for 3d functions in pygame

	Documentation python3d
================================

An open source python library dedicated to pygame for 3d rendering in python 
Author = Abhinav-p

prerequisites:
-------------
numpy
pygame

how to install numpy and pygame
-------------------------------
open up the command terminal and type
pip install numpy
pip install pygame


how to import :
---------------
=>from python3d import p3d
or
=>import python3d

cordinate system of pygame:
----------------------------
(0,0)
----------------------------------->x
|
|
|
|
|
|
|
y

how to use:
------------
inorder to use python3d you must create a 3d object.Each 3d object is unique and can handle multiple 3d shapes and images

==>from python3d import p3d


==>visual3d=p3d(width of display,height of display,display_surface)
note: display surface must be a pygame surface
visual3d is an object of class p3d. It can be anything that the user wants

example:
--------
=>	from python3d import p3d
=>	import pygame
=>	pygame.init()
=>	width=400
=>	height=400
=>	gameDisplay=pygame.display.set_mode((width,height))
=>
=>	visual3d=p3d(width,height,gameDisplay)

inbuilt functions
--============---

1)translate
---------
=parameters:

translate(points,position)
points=>[[x,y,z]] : it describes the positions of the 3d points in 3d space , points parameter takes in an array of points
position=>[x,y,z] : it translates/shifts the origin of the axis by x,y,z values for all those points

=return:
it returns a array of 3 elements [[x,y,z]] which is the position of the points in the new axis system

=example:
=>visual3d=p3d(width,height,gameDisplay)
=>point=[[1,2,3]]
=>point=visual3d.translate(point,[300,100,50]) 

2)Point_Rotation
----------------
rotates a point in 3d space
=parameters:
Point_Rotation(point,alpha,beta,gamma)

point=> [x,y,z]   : 3d cordinates of the point to be rotated with respect to the axis
alpha=> rotation about x axis in radians
beta=>  rotation about y axis in radians
gamma => rotation about z axis in radians

=return:
it returns a array of 3 elements [x,y,z] whih is the position of the point after rotation

example:
=>point=[1,2,3]
=>new_point=visual3d.Point_Rotation(point,1,2,3)

3)rotate_axis
--------------
rotates a collecion /array of points in 3d space continuosly to create a rotating animation about the 3d axis

=>animate /viewing tool 

=parameters:
rotate_axis(array of points,speed of rotation)
array of points=> it is the collection of points to be rotated in 3d space
speed of direction => it is an array : [x,y,z], it describes the speed of rotation in each direction x,y,z 


=return:
it returns an array of points same as input but rotated

=example:
=>points=[[1,2,3],[2,3,4]]
=>new_points=visual3d.rotate_axis(points,[1,2,3])

4)draw_poly
------------

draws a polyon in the 3 diamensional space
-filled polygon ,no fill polygon ,colored

=parameters:

draw_poly(points,color,fill_colors=(0,0,0),fill=False)

points=> an array of points creating the polygon [[x,y,z]]
color=>(r,g,b) value of color of lines of polygon
fill_colors=(r,g,b) color fills the polygon  . only functions if fill=True

=return:
None

=example:
=>points=[[100,100,0],[100,-100,0],[-100,-100,0],[-100,100,0]]
=>visual3d.draw_poly(points,(100,100,200),fill_color=(255,0,0),fill=True)

5)eliminate_diamention
------------------------
it convert a array of 3 diamentional points into normal 2 diamentional system

=parameters:

eliminate_diamention(points)
points= array of 3d points

=return:
points , an array of points in 2 d space [[x1,y1],[x2,y2]]

=example:
=>points=[[2,3,4],[3,4,5]]
=>new_2d_points=eliminate_diamention(points)

6)cube
-------

draws a cube in the 3d space

=parameters:
cube(size,position,color,axis=(0,0,0),rotspeed=(0,0,0),fill=False,color_arr=[],auto_rotate=False):

size=size of the cube, length of side 
position=position of the cube in 3d space . it is with respect to the center of the cube
color=(r,g,b) color of lines
axis= specify the position of origin of the axis
rotspeed= rotates the cube by a (x,y,z) radians if auto_rotate=False
		if auto_rotate=True
		creates a rotating animation  of the cube with speeds(x,y,z) . All x,y,z measured in radians

fill= if set True it fills the cube with *specific* colors for each faces
	required parameter for fill: color_arr

color_arr= if fill is True a array of color has to be passed describing the color of each faces of the cube. it takes parameters in the order :front face,right face,back face,left face,top face,bottom face respectively

=return:
None

=example:
=>color_arr=[(255,255,0),(255,0,0),(255,0,0),(229,138,53),(0,0,255),(229,138,53)]
=>visual3d.cube(100,(0,0,0),(255,255,0),color_arr=color_arr,axis=(width/2,height/2,0),rotspeed=(0.01,0.01,0.01),fill=True)

7)cuboid
---------
draws a cuboid of length,bredth,height in 3d space

=parameters:

cuboid(size,position,color,axis,rotspeed=(0,0,0),auto_rotate=False)

size= a tuple of (length,bredth,height) 
position=position of the cuboid in 3d space . it is with respect to the center of the cuboid

color=color of cuboid(r,g,b)

rotspeed=rotates the cuboid by a (x,y,z) radians if auto_rotate=False
		if auto_rotate=True
		creates a rotating animation  of the cuboid with speeds(x,y,z) . All x,y,z measured in radians

=return:
None

=example:
=>visual3d.cuboid((100,200,300),(0,0,0),(255,0,0),(width/2,height/2,0),(0.01,0.01,0.01))

8)flipY
--------

flips the y axis of the points

=parameters:
flipY(points)
points => a 2d array of points

= return:
points , a 2d array of flipped points

9)flipX
--------

flips the x axis of the points

=parameters:
flipX(points)
points => a 2d array of points

= return:
points , a 2d array of flipped points

10)flipZ
--------

flips the z axis of the points

=parameters:
flipZ(points)
points => a 2d array of points

= return:
points , a 2d array of flipped points


11)trans_rotate
---------------
does translation and rotation at the same time , used for animate purposes and movement of 3d shapes

=parameters:
trans_rotate(points,rotation,axis)
points=array of points describing the object
rotation=[x,y,z] rotation about x,y,z axis
axis=[x,y,z] position of origin of x,y,z space

=return:
points= an 2d array of trans_rotated points 

12)scale
---------
scales up or down the 3d object in the 3d space

=parameters:
scale(points,scales)
points=array of points eg: [[1,2,3],[2,3,4]]
scales=(x,y,z) the amount to be scaled in each axis

=return:
points, array of scaled points


13)create_space
----------------

creates a 3 -diamentional space of creating mutiple 3d drawings under  a single function.3d drawings with mutiple shapes but connected.
explanation and use   ? => it can be used to create virutual 3d world inside pygame. 3d games and enviorments.
user can control the viewing angle and movement controls with mouse and keys specified by the user.
This 3d enviorments acts as a single entity in the program.

=parameters:

create_space(surfaces,colors=[(255,255,255)],keys=[pygame.K_RIGHT,pygame.K_UP,pygame.K_a,pygame.K_LEFT,pygame.K_DOWN,pygame.K_s],z_extrema=2000,fill_colors=[(0,0,0)],rotation=(0,0,0),axis=(0,0,0),space_translate=(100,100,0))

surfaces= it is a array of array of points describing each surface
eg:  surfaces=[[[100,100,100],[200,300,200]],[[299,299,19],[199,299,100]]]
      this contains two surfaces

colors=array of colors for each surface. required parameter for more than one surface [(r,g,b),(r,g,b)]

keys=control keys . its controls the movement of axis for the surface elements only  ie these keys move surface elements in left,right ,up,down directions pygame.K_a ans pygame.K_s describes z axis motions. zoom in and out

z_extrema=it is a optional parameter which tells the code to ignore surfaces having z cordinate greater than the z_extrema

fill_colors= array of colors for filling the surfaces
		while giving colors ,surfaces and colors have to be arranged in the increasing order of priority. ie, which shapes to be seen when overlapping occurs
rotation= (x,y,z) rotation about axis

axis=(x,y,z) position of origin for this surfaces

space_translate=(x,y,z) translates the space cordinates origin to a specified value

=return:
--------
None

=example:

left_wall=[[-100,-100,0],[-100,100,0],[-100,100,500],[-100,-100,500]]
backwall=[[-100,-100,0],[400,-100,0],[400,100,0],[-100,100,0]]
right_wall=[[400,-100,0],[400,100,0],[400,100,500],[400,-100,500]]
frontwall=[[-100,-100,520],[400,-100,520],[400,100,520],[-100,100,520]]
roof1=[[-150,-200,300],[450,-200,300],[450,-90,600],[-150,-90,600]]
roof2=[[-150,-200,300],[450,-200,300],[450,-90,-30],[-150,-90,-30]]
surface=[backwall,left_wall,right_wall,roof2,frontwall,roof1]
colors=[(255,255,255),(255,255,255),(255,255,255),(255,255,255),(255,255,255),(255,255,255)]
color_arr=[(255,255,0),(255,0,0),(255,0,0),(229,138,53),(0,0,255),(229,138,53)]
visual3d.create_space(surface,colors=colors,fill_colors=color_arr,space_translate=(width/2,height/2,0))


14)rotate:
-----------
rotates points to a fixed angle with no animation

=parameters:
rotate(points,rotation)
points=array of points [[1,2,3]]
rotation=[x,y,z]  angle with x,y,z in radians

=return:
new_rotated_points

15)key_translate:
-----------------

translates based on key inputs

=parameters:
key_translate(keys,points,translate_from=(0,0,0),speed=(0.5,0.5,0.1))

keys=keys for translation [x+,y+,z+,x-,y-,z-] 
      x+ incresesx
      y+ increses y
      z+ increses z

points= array of points for translation

translate_from=initial position of origin

speed=rate of translation for each axis (x,y,z)

=return:
array of translated points


16)image:
-----------

translates and rotates a pygame image and displays it in 3d space
note: images should be 2d they are being visualised in 3d

=parameters:
image(image_object,position,width,height,corner_depth=(0,0,0),rotation=(0,0,0)):

image_object= pygame image surface
position=position of image, width,height has usual meaning

corner_depth=depth of other 3 corners with respect to first one

return:
None


=example:

bird_img=pygame.image.load("bird.png")
visual3d.image(bird_img,(width/2,height/2,0),100,100,rotation=(x/100,y/100,x/100))


17)image_space
--------------

creates a 3d space of images, each image acts as a part of a entire structure

=parameters:
image_space(images,positions,keys=[pygame.K_RIGHT,pygame.K_UP,pygame.K_a,pygame.K_LEFT,pygame.K_DOWN,pygame.K_s],z_extrema=2000,rotation=(0,0,0),axis=(0,0,0),space_translate=(100,100,0)):

parameters have similar meaning as for create_space and image functions

=return:
None

=example:
bird_img=pygame.image.load("bird.png")
wall=pygame.image.load("wall.jpg")
roof=pygame.image.load("roof.jpg")

points=[[100,100,0],[100,-100,0],[-100,-100,0],[-100,100,0]]
left_wall=[[-100,-100,0],[-100,100,0],[-100,100,500],[-100,-100,500]]
backwall=[[-100,-100,0],[400,-100,0],[400,100,0],[-100,100,0]]
right_wall=[[400,-100,0],[400,100,0],[400,100,500],[400,-100,500]]
frontwall=[[-100,-100,520],[400,-100,520],[400,100,520],[-100,100,520]]
roof1=[[-150,-200,300],[450,-200,300],[450,-90,600],[-150,-90,600]]
roof2=[[-150,-200,300],[450,-200,300],[450,-90,-30],[-150,-90,-30]]
positions=[backwall,left_wall,right_wall,roof2,frontwall,roof1]
images=[wall,wall,wall,roof,wall,roof]

visual3d.image_space(images,surface,z_extrema=10000,rotation=(0.001,0,0),space_translate=(width/2,height/2,0))
p3d.image_space(images,surface,z_extrema=10000,rotation=(0.001,0,0),space_translate=(width/2,height/2,0))

note=: this function is still under development and sometimes may not work properly


about this library:
===================
this library is still under development and can be used for many purposes including 3d visualisations in pygame.
pygame is a simple 2d game development module for python

hope that this library helps you

numpy and pygame:
===================
both these libraries are used as standard ones and each of them has their own licenses


