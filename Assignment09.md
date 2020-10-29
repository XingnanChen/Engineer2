
## Assignment 09 Write-up  

### Downloads: 

[MyGame_x86](https://github.com/XingnanChen/Engineer2/blob/master/Assignment09/MyGame_x86.zip?raw=true)  
[MyGame_x64](https://github.com/XingnanChen/Engineer2/blob/master/Assignment0/MyGame_x64.zip?raw=true)  

### ScreenShots  
Game Running  
![Image](Assignment09/gamerunning.gif)  

### Implementation:  
This assignment is to create human readable effect lua file and build a binary effect file from this lua file to improve the performance.  
- Create a human readable effect lua file: 
```
return
{
	vertexShaderPath = "Shaders/Vertex/standard.shader",
	fragmentShaderPath = "Shaders/Fragment/myShader.shader"
}
```  



Show us a human-readable Effect file
Show us the binary version of the same Effect file (a screenshot from a hex editor is fine if it's readable)
Explain how your run-time code knows where the second path in the file starts
Tell us whether the paths you store are relative to $(GameInstallDir) or $(GameInstallDir)/data. Explain why you made this decision. (You must explain the advantages and disadvantages of your choice or else you will lose points.)
Show us how you extract the two paths at run-time
(You should still show a screenshot to keep your readers interested even though nothing is different visually)
