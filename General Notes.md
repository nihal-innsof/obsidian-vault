## IMPORTANT WINDOWS COMMANDS
##### Connect flutter application in emulator connect to server running in wls2 ubuntu
Add the following code in *PowerShell*. The following code does a port forwarding from windows to the wsl2 instance, so the server is visible to the emulator.
```powershell
netsh interface portproxy add v4tov4 listenaddress=0.0.0.0 listenport=3000 connectaddress=<WSL Ubuntu Ip address> connectport=<WSL Ubuntu Port>
```
[Reference](https://learn.microsoft.com/en-us/windows/wsl/networking?source=recommendations#accessing-a-wsl-2-distribution-from-your-local-area-network-lan)
### Flutter app flavors
* Development: As the name suggests.
* Staging: Used to test out implemented feature by team or stake holders
* Production: Passed to the end user. (Final Product)