Osamuyi Uwadia
Windows 

First Since I am using a Windows OS
I had to use Getting started with Raspberry Pi Pico 9.2 at https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf
To install the Toolchain, I had to install some toll to build 
•	Arm GNU Toolchain (you need the filename ending with -arm-none-eabi.exe) 
o	During installation you should tick the box to register the path to the Arm compiler as an environment variable in the Windows shell when prompted to do so.
•	 CMake 
o	During the installation add CMake to the system PATH for all users when prompted by the installer
•	Build Tools for Visual Studio 2022 
o	When prompted by the Build Tools for Visual Studio installer you need to install the C++ build tools only.
•	Python 3.10 
o	During the installation, ensure that it’s installed 'for all users' and add Python 3.10 to the system PATH when prompted by the installer. You should additionally disable the MAX_PATH length limit when prompted at the end of the Python installation.
•	Git
o	When installing Git you should ensure that you change the default editor away from vim,
•	Then using my VS Code’s integrated terminal that is using the Windows PowerShell Terminal I used this code:
•	I opened the Development Command Prompt for VS 2022
•	Then I cd in Terminal to my downloads folder 
o	C:\Users\pico\Downloads> git clone -b master https://github.com/raspberrypi/pico-sdk.git 
o	C:\Users\pico\Downloads> cd pico-sdk C:\Users\pico\Downloads\pico-sdk> git submodule update --init 
o	C:\Users\pico\Downloads\pico-sdk> cd .. C:\Users\pico\Downloads> git clone -b master 
o	https://github.com/raspberrypi/pico-examples.git
This allowed me to get the SDK and examples.
Next, I  set the path to the SDK as follows, C:\Users\pico\Downloads> setx PICO_SDK_PATH "..\..\pico-sdk"
I closed my Development Command Prompt for VS 2022 and open a second Developer Command Prompt window
I would then navigate through the second Developer Command Prompt window
By using this: 
o	C:\Users\pico\Downloads> cd pico-examples
o	C:\Users\pico\Downloads\pico-examples> mkdir build 
o	C:\Users\pico\Downloads\pico-examples> cd build 
o	C:\Users\pico\Downloads\pico-examples\build> cmake -G "NMake Makefiles" .. C:\Users\pico\Downloads\pico-examples\build> nmake
This code is from 9.23
 ![image](https://user-images.githubusercontent.com/114784563/195963974-008007d2-74a3-4638-ae4e-89dbe0923fcb.png)

	It will look like this, and it is a longer process
I opened Visual Studio 
Then I used looked at this video(https://www.youtube.com/watch?v=K0LNCunQZUw) in combine of looking at( sudong-wang/ese5190-lab2)
I followed 9.2.4
Then in the Settings pane click on "Extensions" and then "CMake Tools
I scrolled down to "Cmake: Configure Environment". Click on "Add Item" and set the PICO_SDK_PATH to be ..\..\pico-sdk as
 Close the Settings page and go to the File menu and click on "Open Folder" and navigate to pico-examples repo and click "Select Folder". Select "GCC for arm-none-eabi" for your compiler.
 	![image](https://user-images.githubusercontent.com/114784563/195963993-eb0c9ada-e5fa-4c7f-a568-c6b83cdcebd4.png)

You will get another one of these 
![image](https://user-images.githubusercontent.com/114784563/195964003-e9c1c240-47fe-40f0-a37b-2f57c6fef3cd.png)

After that you can drag your hello_usb.uf2 our RP2040 that will be boot mode 
![image](https://user-images.githubusercontent.com/114784563/195964007-8c21adb9-c732-4d45-b560-aac8234c2103.png)
 

Open up Putty (Serial) and this will be your outcome:
