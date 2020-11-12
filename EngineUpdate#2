# Engine Update \#2


This Week, I used XInput and made my engine support gamepad input.    

At first, I created a Enum called eGamepadKeyCodes to make users understand the input easily.  
```cpp  
eGamepadKeyCodes
{
  A,
  B,
  X,
  Y
};
```  

Then I overloaded the BindActions function to bind the gamepad button to the functions:  
```cpp
void BindActions(UserInput::KeyCodes::eGamepadKeyCodes i_key, eInputEvent i_inputEvent, std::function<void()> callback);
```

Here is how users use the gamepad as input:  
```cpp
gController.BindActions(UserInput::KeyCodes::A, e_pressed, [&]() { objectMoveUp = -1.f; });
gController.BindActions(UserInput::KeyCodes::A, e_released, [&]() { objectMoveUp = 0.f; });
```  

Next week, I will work on BindAxis to bind user-defined function to the axis.  

```cpp  
enum eMouseAxis{
  MouseX,
  MouseY
}
enum eGamepadAxis
{
  GamepadLX,
  GamepadLY,
  GamepadRX,
  GamepadRY
};
```   

The interface is:  

```cpp
void BindAxis(eMouseAxis i_key, eInputEvent i_inputEvent, std::function<void(float)> callback);
void BindAxis(eGamepadAxis i_key, eInputEvent i_inputEvent, std::function<void(float)> callback);
```  
