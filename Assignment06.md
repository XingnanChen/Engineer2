## Assignment 06 Write-up

### Downloads: 

[MyGame_x86](https://github.com/XingnanChen/Engineer2/blob/master/Assignment06/MyGame_x86.zip?raw=true)  
[MyGame_x64](https://github.com/XingnanChen/Engineer2/blob/master/Assignment06/MyGame_x64.zip?raw=true)


### Assignment Objectives：
- Using Lua to create a human-readable mesh file and loading the meshes.  

### ScreenShots
Game Running  
![Image](Assignment06/gamerunning.gif)  

We can see from the gif the user can move the camera around by w,a,s,d and can control the above object with arrow keys.  
When user press F4. The mesh above will switch it's mesh from a square to a triangle.  

### Implementation:  
- Human-readable mesh file  
Many people perhaps have access to the asset files. Making asset files that are human-readable is to make it easy to create or edit by others.    
This is how I make my human-readable mesh file:  
```
return
{
	-- every three value in the vertexData array is a vertex data
	-- the vertex is in x, y, z order,
	vertexData = {
		0,	0,	0, 
		0.8,	0,	0, 
		0.8,	-0.8,	0, 
		0,	-0.8,	0
	},

	-- every three value in the indexData array are the vertex indexes of a triangle
	-- the vertices is in right-hand order,
	indexData = {
		0,	1,	2,
		0,	2,	3
	}
}
```  
It is easy to read as I added some comments and made a organized format. It is also keep the efficient for the machine. 

- Loading the meshes  
Using the same logic in the example lua project to load the meshes.  

This is the screenshot for debugging mesh builder  
![Image](Assignment06/debug.png)    

###Fixed bugs  
- Initialize the meshes and effects(the game won't crash right now): Meshes and effects are no longer loaded dynamically.  
- The object moves fast in x64: Reason: Implement the movement in the wrong function(SubmitDataToBeRendered).  Fixed: Implement it in UpdateSimulationBasedOnTime.   
