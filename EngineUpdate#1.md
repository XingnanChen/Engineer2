# Engineer2


This Week, I finished the implementation of the BindAction() interface.

The function's signature is 
```cpp

enum eInputEvent
{
	e_pressed,
	e_released
};

//i_key:        the input key representation, for now it's the same as the type i_keyCode from the UserInput Module.
//i_inputEvent: the key event representation, it only support two events now, e_pressed means key is pressed, e_released means the first time the key is released.
//callback    : the callback function that will bind to the key.
void BindAction(uint_fast8_t i_key, eInputEvent i_inputEvent, std::function<void()> callback);
```

I searched a lot for implementing a delegate system in mordern C++ at first, but it turns out the binding functionality the controller(or user input) system needed only 
accept void() signature callback, so I don't have to implement a complicate template delegate system. Though the delegate system is really helpful for user to write complex logics in game, 
that's beyond this project (If I have time, I may implement this as a side project).

now user can use the interface like:  
```cpp
	auto& gController = sController::g_controller;

	gController.BindActions('W', e_pressed, [&]() { cameraMoveUp = 1.f; });
	gController.BindActions('A', e_pressed, [&]() { cameraMoveLeft = -1.f; });
	gController.BindActions('D', e_pressed, [&]() { cameraMoveLeft = 1.f; });
	gController.BindActions('S', e_pressed, [&]() { cameraMoveUp = -1.f; });
	
	gController.BindActions('A', e_released, [&]() { cameraMoveLeft = 0.f; });
	gController.BindActions('D', e_released, [&]() { cameraMoveLeft = 0.f; });
	gController.BindActions('S', e_released, [&]() { cameraMoveUp = 0.f; });
	gController.BindActions('W', e_released, [&]() { cameraMoveUp = 0.f; });
```


What's more, I also added these two values to UserInput::KeyCodes enum.
```cpp 
				MouseLButton = 0x01,
				MouseRButton = 0x02
```

which means the system now support button click event. It seems UserInput::KeyCodes from UserInput.h is not platform-independent. Next week I'll make it platform independent.

For Gamepad support, it seems there is no general c++ SDK for controller on windows, which means you have to search specific method once you want to add a specific controller to the engine.
For xbox 360 controller, we can just develop with Xinput(https://docs.microsoft.com/en-us/windows/win32/xinput/xinput-and-directinput).
For dual shock 4(ps4 controller), there is no easy way to add support for it, since there is no official sdk for it(no need since it's not designed for Windows platform).
Refering to the library(https://github.com/jibbsmart/JoyShockLibrary). If we want to add support from scratch, we have to use cross platform HID api(https://github.com/signal11/hidapi)
to write decent platform-independent code. 

So I decide only support xbox 360 controller for Windows and try to make the interface platform-independent, though there is only xbox 360 support for windows.
