---
layout:     post   				    # 使用的布局（不需要改）
title:      Updating Xcode 10.2.1 				# 标题
subtitle:   Worst Decision Today #副标题
date:       2019-06-10 				# 时间
author:     JZ 						# 作者
header-img: img/Xcode_on_laptop.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - Software
    - Life
    - Xcode
---

## What Happened?
I have done the Map Scene for my UWParking App this morning, testing the App on the simulator became more difficult than before; as a result, I would like to use my iPhone X to do the test job. The versin of Xcode that I was using is 10.1; however, I had updated my iPhone to 12.3.1 few days ago, so the Xcode didn't support this behavior. I have no choice but update my Xcode to 10.2.1 which I really didn't want. After the software had been updated, something terrible happened. One of the frameworks that I am using which was provided by <a href="https://github.com/meteochu">Andy Liang</a> named <a href="https://github.com/meteochu/WatSwift">WatSwift</a> isn't supported by the latest version of Xcode. As a result, I have to rollback to the Xcode 10.1. What a "good" decision today.
