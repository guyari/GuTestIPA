---
layout: page
title: About
tagline: 运用 GitHub + jekyll 承载 ipa 的存储使 iPhone 得以 OTA 下载使用
permalink: /about.html
---


## 使用

1. 使用 Xcode 打好 Development 包，获取 ipa 文件
2. 把 ipa 文件以及项目的图标上传到 GitHub 并获取地址
3. 根据上述地址填写相关信息，生成 `manifast.plis` 文件（这个文件也可由第一步打包时填写生成）
4. 把 `manifast.plis` 文件上传，获取其地址
5. 生成最后 iPhone 能用的下载地址，格式如下： <br/>
`itms-services://?action=download-manifest&url=manifest.plist的地址`
6. 最后使用 GitHub Page 引用这个地址，写成一个页面，手机端 safari 浏览器打开，点击安装

若在打包时勾选了 **Incloud manifest for over-the-air installtion** 的话，会让你输入 ipa的下载地址、图标的地址等信息，最后会生成 plist 文件，这样就不用自己手动新建啦

![xcode-step](https://raw.githubusercontent.com/1ilI/1ilI.github.io/master/resource/2018-04/xcode-step.png)

最后的 `manifast.plis` 文件，手写也行，生成的也可，其中内容可如下所示：
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>items</key>
	<array>
		<dict>
			<key>assets</key>
			<array>
				<dict>
					<key>kind</key>
					<string>software-package</string>
					<key>url</key>
					<string> ipa文件的地址 </string>
				</dict>
				<dict>
					<key>kind</key>
					<string>display-image</string>
					<key>url</key>
					<string> 图标地址（小图，可用一个） </string>
				</dict>
				<dict>
					<key>kind</key>
					<string>full-size-image</string>
					<key>url</key>
					<string> 图标地址（大图，可用一个） </string>
				</dict>
			</array>
			<key>metadata</key>
			<dict>
				<key>bundle-identifier</key>
				<string> Xcode上对应的 Bundle Identifier </string>
				<key>bundle-version</key>
				<string> Xcode上对应的 Version </string>
				<key>kind</key>
				<string>software</string>
				<key>title</key>
				<string> Xcode上对应的 Display Name </string>
			</dict>
		</dict>
	</array>
</dict>
</plist>
```

[返回首页]({{ site.url }}{{ site.baseurl }})
