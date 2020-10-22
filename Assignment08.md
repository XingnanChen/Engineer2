
## Assignment 07 Write-up  

### Downloads: 

[MyGame_x86](https://github.com/XingnanChen/Engineer2/blob/master/Assignment08/MyGame_x86.zip?raw=true)  
[MyGame_x64](https://github.com/XingnanChen/Engineer2/blob/master/Assignment08/MyGame_x64.zip?raw=true)  

### ScreenShots  
This assignment is to build a binary mesh file to reduce the loading mesh time.
Game Running  
![Image](Assignment08/gamerunning.gif)  

### Implementation:  
- Using .lua to generate a binary file in MeshBuilder.    
	The example of a binary geometry file built by MeshBuilder:   
![Image](Assignment08/binary.png)   
  The Order of the four things is VertexCount, VertexPositionData, IndexCount, IndexData. By giving the count of the vertices and I already know that one vertex has 4 bytes, I can write the index count next to the last vertex position data easily.  
  
	Using binary file formats, we can save a lot of space on the disk. Comparing with the human-readable files, we only have data in the binary file. And using lua files will cost more time than using binary files. 

补充：：Please present the differences in size and speed in a way that is easy for your readers to understand 。Don't just show some table without explaining why it's relevant. Help your readers to understand how the results demonstrate the advantages of binary files.

Create a mesh in Maya with a large number of vertices and indices to measure the advantages of binary files
A helix is a good choice for this because there are many parameters that can greatly increase the vertex/index count. Make it have as many as you can that will still fit within the limits of uint16_ts and 16-bit indices. You don't need to commit this to git; just make it temporarily to do measurements for your write-up and then delete it.
If you complete the optional challenge to support 32-bit indices you can also compare a geometry with 32-bit indices, but you should still do the comparison for a geometry with 16-bit indices
Tell us how big (in bytes) the human-readable version is on disk and how big (in bytes) the binary version is on disk
Tell us how long it takes to load the human-readable version and how long it takes to load the binary version
You can use functions from the Time project for this. Make this temporary code and revert it after you have made measurements!
To time the human-readable version put timing code in MeshBuilder. Make sure to time not just how long it takes to load the Lua file but how long it takes to extract the data. (You should start timing right before loading and end timing right before writing out the binary file.) You can put a temporary print statement with the total time that will show up in Visual Studio's Output window.
To time the binary version put timing code in your run-time mesh loading code. Make sure to time not just how long it takes to load the binary file but how long it takes to extract the data. You can put in a temporary logging statement with the total time that will show up in your log file.
When measuring run-time performance double-click the EXE to run the game rather than attaching a debugger. The debugger can make the game run more slowly than it otherwise would.
Make sure to do this timing on a release build! (It doesn't matter which platform you time, though.)

uint32_t和float的东西：Tell us whether the built binary geometry files should be the same or different for the different platforms, and explain why. (In other words, should the binary file for a specific mesh that your MeshBuilder outputs for Direct3D be the same as the one that it outputs for that same mesh in OpenGL? If so, explain why. If not, explain why there are differences and what they are.)

- Load the binary file at run-time  
Extract the four pieces of data from binary data at run-time 
```cpp
memcpy(&vertexCount, reinterpret_cast<void*>(currentOffset), curSize);
				currentOffset += curSize;
				newMesh->vertexCount = vertexCount;

				newMesh->vertexData = new VertexFormats::sVertex_mesh[vertexCount];
				curSize = sizeof(VertexFormats::sVertex_mesh) * vertexCount;
				memcpy(newMesh->vertexData, reinterpret_cast<void*>(currentOffset), curSize);
				currentOffset += curSize;

				curSize = sizeof(indexCount);
				memcpy(&indexCount, reinterpret_cast<void*>(currentOffset), curSize);
				currentOffset += curSize;
				newMesh->indexCount = indexCount;

				newMesh->indexData = new uint16_t[indexCount];
				curSize = sizeof(uint16_t) * indexCount;
				memcpy(newMesh->indexData, reinterpret_cast<void*>(currentOffset), curSize);
  ```

