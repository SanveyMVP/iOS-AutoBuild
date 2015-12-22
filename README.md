# iOS-AutoBuild
iOS实现脚本自动打包
readme
这是一个简单地自动打包脚本

#简单的目录结构
进入debug文件
	
```
test-$ ls

debug.plist				debug.sh

```
其中
*  debug.sh  
打包脚本 改脚本会读取 和他同名的plist文件中的配置信息进行打包。打出的ipa包得命名是以appName_version_gitCommitID  appName 和 version 可以在 同名的 plist文件中修改  不过 这连个字段中的 . 会被替换成为 _。
脚本执行后创建一个名为version的文件夹 在此文件夹下有 AppFile  BuildDir  DSYM   IPA 四个文件夹。他们中存放的分别是 AppFile 存放打包后的app文件  BuildDir 存放打包生成的 xcarchive文件 DSYM 存放打包的DSYM文件 IPA 存放打包成功的IPA文件
*  debug.plist
脚本需要的配置信息



#使用方法
使用方面重要的工作就是配置plist文件




key 				| 是否必填	   | 作用 
---------  		| --- 		| -------------
identifier 		| 是 			| bundle id 
version 			| 是 			| 版本号
p12 				| 是 			| p12文件 相对于sh脚本的位置 
p12Password   	| 否 			| p12文件的密码 没有可以不填写 
mobileprovisionFile | 是  | 描述文件 相对于sh脚本的位置
appName 			| 是 			| ipa的英文名称
conf				| 是			| 打包环境 Debug Release 等
plistInfo		| 是			| 所要打包的工程文件的info.plist 这需要相对路径 
bundleDisplayName|是			| ipa安装后的的现实的名称
xcworkspace		| 是			| workspace的相对路径
scheme			| 是			| scheme的名称

配置成功后
cd 到此文件夹下 执行 sh debug.sh 


可以扩展的功能还有很多。欢迎扩展。
计划中扩展
*  实现itms-services协议企业内发布或者越狱发布
*  自动发送邮件


