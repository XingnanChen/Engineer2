
## Assignment 07 Write-up  

### Downloads: 

[MyGame_x86](https://github.com/XingnanChen/Engineer2/blob/master/Assignment07/MyGame_x86.zip?raw=true)  
[MyGame_x64](https://github.com/XingnanChen/Engineer2/blob/master/Assignment07/MyGame_x64.zip?raw=true)  

### ScreenShots  
Game Running  
//截图gif  
![Image](Assignment07/gamerunning.gif)  

### Implementation:  
- Install Maya and attach Maya to Visual Studio.  
Install Maya and set environment variables to tell Maya the location of plugins and devkit. Add MayaMeshExporter project into Visual Studio and add the references.加（Tell us what references you had to add to the MayaMeshExporter project，Tell us what other projects depend on MayaMeshExporter). Build the project, then Maya can use the plugins from Visual Studio. Attach Maya to Visual Studio, then those plugins can be debugged in Visual Studio when we use Maya.  
(加截图：Show a screenshot of you debugging your plug-in. The requirement here is to show Visual Studio attached, and the little yellow arrow somewhere in your plug-in code to prove that it is actually loaded (along with its symbols)  
Try to not show your actual code that writes out the mesh (so that it doesn't give away the homework to other students). You may consider taking a screenshot of the debugger in initializePlugin() or writer() rather than in WriteMeshToFile().)  

- Create meshes by Maya and use them in Visual Studio.  
Create the meshes in Maya and then export them in my project. I only export the data that matched my human-readable file. (解释：Tell us whether you exported the unused data (e.g. normals, tangents, bitangents, texture coordinates) to your human-readable file or not. Explain why you made this choice.） 
When I tried to load a model with too many vertices, (加说明：Tell us what happens if you try to load a model with too many vertices. Your code should gracefully handle this rather than crash or render something incorrectly.)  


- Depth buffering  
Using depth buffering to (目的：)
