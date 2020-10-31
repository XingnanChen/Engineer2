## Controller Engine  
 
A game controller is an input device(keyboard, mouse, gamepad) to provide input to a video game, typically to control an object or character in the game.   

Making a controller engine is easy for users to get the inputs from different devices and control the objects by inputs.  

My project is to create a controller engine that can:   
Get inputs from different devices(keyboard, mouse, gamepad)  
Provide the interface that users can bind the inputs with users’ functions. Users can use the interfaces from this engine to control the objects easily.  

Hardware input from a player commonly includes key presses, mouse clicks. I referred to UE4’s input interface:  
ControllerEngine->BindAction(InputKey key, InputEvent keyEvent, Function func) is bound to event-driven behavior.   
key: Enum type, the value of the input key.   
keyEvent: Enum type, representing the key’s state, such as pressed or released.  
func: user-defined function.  
This function is used to bind the input key and its state to the user-defined function. The Function type definition is the most complicated to implement. After some early research(https://stackoverflow.com/questions/48967706/how-to-pass-stdfunction-with-different-parameters-to-same-function ), std::function and variadic template will be used to solve this problem.  

I am looking forward to making a user-friendly controller game engine to deal with the inputs. I will focus on providing interfaces with inputs from the keyboard and mouse first.   

If I have extra time, I will make this engine support the mouse movement. In order to support this, I need another interface: ControllerEngine->BindAxis(InputAxis axis, Function func), which is bound to continuous game behavior. And I will make this engine support gamepad input.  

