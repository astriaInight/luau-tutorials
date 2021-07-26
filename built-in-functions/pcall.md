# pcall
## What is pcall?
pcall is a built-in function in lua. The function name stands for "Protected Call". pcall is used for error handling. The main use of this is to test if a line of code errors or runs with no errors. You can also read the error message.

## When should I use it?
pcall should be used for error handling. This includes checking if an HTTP request was sent correctly, checking if user input is valid, etc.

## How does it work?
pcall runs a function and returns two variables. The first variable is a boolean (true or false) that tells you if the function ran without errors. The second variable is a string that contains an error message, or nil if the function ran without errors.

# Examples
## HttpRequest
```lua
local function sendRequest()
  httpService:GetAsync("https://google.com")
end

local success, errorMessage = pcall(sendRequest)

if not success then
  print("There was an error sending a request: " .. errorMessage)
end
```
#### or you can also put the function directly in the pcall
```lua
local success, errorMessage = pcall(function()
  httpService:GetAsync("https://google.com")
end)

if not success then
  print("There was an error sending a request: " .. errorMessage)
end
```
