## 导入其他 Sikuli 脚本（重用代码和图像）

当您对脚本编写有更多的经验，或者习惯于将解决方案构建成模块化系统时，您可能也希望能够访问编程环境的相关功能——在本例中支持模块化的Python/Jython功能。

这在Sikuli X中是可能的：

- sikuli与Python导入完全兼容


- 从jar文件中导入python模块结构，包括底层Java类，该jar文件使用函数load（jar文件）动态加载


- 自动访问导入的sikuli中包含的图像（无需使用setBundlePath()） 

注意：目前无法导入.skl。作为一种规避措施，您可以动态地将.skl解压（例如，在命令行上使用gzip）到您选择的位置作为.sikuli（例如，temp目录）并从那里导入。



先决条件：

包含您的文件的目录/文件夹。要导入的.sikuli必须在sys.path中（用法见下文）

导入时，Sikuli会自动在同一目录中查找其他Sikuli脚本

导入的脚本必须包含（建议：作为第一行）以下语句：from sikuli import*（这是Python环境了解sikuli类、方法、函数和全局名称所必需的）



用法：

- 将Sikuli模块的路径添加到sys.path（从X-1.0rc3开始：如果要导入的模块与主脚本位于同一目录中，请跳过此步骤。）

- 只用名字导入你的.sikuli。例如，导入a_module.sikuli只需编写import a_module。

- 该示例包含避免双重输入的建议：

  ```python
  # an example - choose your own naming
  # on Windows
  myScriptPath = "c:\\someDirectory\\myLibrary"
  # on Mac/Linux
  myScriptPath = "/someDirectory/myLibrary"
  
  # all systems
  if not myScriptPath in sys.path: sys.path.append(myScriptPath)
  
  # supposing there is a myLib.sikuli
  import myLib
  
  # supposing myLib.sikuli contains a function "def myFunction():"
  myLib.myFunction() # makes the call
  ```



