# UbaSessionServerDisabling-
How to disabling UbaSessionServer in Unreal Engine 5 (In particular 5.5.0)
this is a mini guide about disabling UbaSessionServer in Unreal Engine 5 (In particular 5.5.0)

Let's start the debriefing with compiling the code. The compiler will output the path to the UnrealBuildTool log file (In my case) C:\Users\RootTool\AppData\Local\UnrealBuildTool\Log.txt

Next, opening the file, we will see the first lines:
```
C++
No config file at C:\ProgramData\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml
 
No config file at C:\Users\RootTool\AppData\Local\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml
 
No config file at C:\Users\RootTool\Documents\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml
 
Configuration will be read from:
  C:\Users\RootTool\AppData\Roaming\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml
No config file at C:\ProgramData\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml No config file at C:\Users\RootTool\AppData\Local\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml No config file at C:\Users\RootTool\Documents\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml Configuration will be read from: C:\Users\RootTool\AppData\Roaming\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml
The build configuration will be selected from: C:\Users\RootTool\AppData\Roaming\Unreal Engine\UnrealBuildTool\BuildConfiguration.xml.
```

Let's open this file:

XML
```
<?xml version="1.0" encoding="utf-8" ?>
<Configuration xmlns="https://www.unrealengine.com/BuildConfiguration">
	<BuildConfiguration>
	</BuildConfiguration>
</Configuration>
```

And just add 2 lines:

XML
```
<bAllowUBAExecutor>false</bAllowUBAExecutor>
<bAllowUBALocalExecutor>false</bAllowUBALocalExecutor>
```
For the file to become:

XML
```
<?xml version="1.0" encoding="utf-8" ?>
<Configuration xmlns="https://www.unrealengine.com/BuildConfiguration">
	<BuildConfiguration>
		<bAllowUBAExecutor>false</bAllowUBAExecutor>
		<bAllowUBALocalExecutor>false</bAllowUBALocalExecutor>
	</BuildConfiguration>
</Configuration>
```
Personally, after that UbaSessionServer didn’t bother me at all, and compilation returned to the previous 30 seconds (8GB of RAM)

Source:
https://dev.epicgames.com/community/learning/tutorials/9dv9/unreal-engine-disable-ubasessionserver-uba
