# 应用介绍

Lookin 是一款 macOS 软件，它可以查看与修改 iOS App 里的 UI 对象，类似于 Xcode 自带的 UI Inspector 工具，或另一款叫做 Reveal 的软件。

此外，虽然 Lookin 主体是一款 macOS 程序，它亦可嵌入你的 iOS App 而单独运行在 iPhone 或 iPad 上。

**Lookin 完全免费。**



#配置方法

### 使用 CocoaPods

1. 在 Podfile 中添加以下内容：

   `pod 'LookinServer', :configurations => ['Debug']`

   这里指定了只有在 Debug 模式下才能使用 Lookin。

2. 运行 `pod install` 或 `pod update LookinServer`

3. 打开 Lookin ，即可查看或调试应用界面。



### 手动设置

1. [点击这里](https://cdn.lookin.work/download/framework/LookinServer-0-9-3.zip) 下载 *LookinServer-0-9-3.zip*，解压后会出现 *LookinServer.framework* 文件，请把该文件移动到你的 iOS 项目的根目录内，即与 *"xxx.xcodeproj"* 位于同一目录。

   ![img](https://cdn.lookin.work/public/style/images/independent/integration-manual-0.jpg)

2. 打开你的 iOS 项目，按照下图步骤所示，选中要使用 Lookin 的 iOS Target，导航至 *Build Settings* 里的 *Framework Search Paths*，然后在 *Debug* 选项里添加 `$(SRCROOT)`

   \* 如果你在上一步没有把 *LookinServer.framework* 复制到项目根目录，而是复制到了别的地方（比如复制到了项目根目录下的 *FavoriteFrameworks* 文件夹），则这里就要把 *"$(SRCROOT)"* 改为 *"$(SRCROOT)/FavoriteFrameworks"*

   ![img](https://cdn.lookin.work/public/style/images/independent/integration-manual-1.jpg)

3. 按照下图步骤所示，导航至 *Build Settings* 里的 *Other Linker Flags*，然后在 *Debug* 选项里添加 `-ObjC -weak_framework LookinServer`

   ![img](https://cdn.lookin.work/public/style/images/independent/integration-manual-2.jpg)

4. 按照下图步骤所示，导航至 *Build Settings* 里的 *Runpath Search Paths*，确认这里已经添加过了 `@executable_path/Frameworks`

   如果没有添加过，请手动添加 *"$(inherited) @executable_path/Frameworks"*（不包含引号）

   ![img](https://cdn.lookin.work/public/style/images/independent/integration-manual-3.jpg)

5. 按照下图步骤所示，导航至 *Build Phases*，点击左上角加号，选择 *New Run Script Phase* 创建一个新脚本。

   将新建的脚本重命名为 *Integrate Lookin*，然后复制 [这段内容](https://lookin.work/faq/integration-manual/run-script-cn.html) 作为脚本的内容。

   ![img](https://cdn.lookin.work/public/style/images/independent/integration-manual-4.jpg)

6. 运行 App，即可正常使用 Lookin 。

