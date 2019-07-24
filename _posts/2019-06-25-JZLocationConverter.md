---
layout:     post   				    # 使用的布局（不需要改）
title:      iOS Coordinate Transform 				# 标题
subtitle:   JZLocationConverter #副标题
date:       2019-06-25 				# 时间
author:     JZ 						# 作者
header-img: img/hold_ios_map.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - iOS Frameworks
    - iOS Development
---

## The Probelm

Recently, I am developing an iOS App about real-time parking information in my University. I designed a map function in my App; however, when I used CLLocation to acquire my test-user's location something went wrong. The coordinate that gained from the CLLocation was different from the user's real location where showed on the map. I had no idea what happened. I double checked my implementation but found nothing wrong, so I started looking for the answer online. After I browsed a bunch of posts, I learned that it was because of my current location. I am in China Mainland right now, and the Chinese government use the different coordinate system from the international standard.

## How to solve the problem

I chanced upon a framework that design by <a href="https://github.com/JackZhouCn">Jack Zhou</a> named <a href="https://github.com/JackZhouCn/JZLocationConverter">JZLocationConverter</a>. He has designed a algorithm that could convert the WGS-84 coordinate into GCJ-02 coordinate and vice versa. This framework is available in both Object-C and Swift. This is not a perfect solution to the coordinate problem but you could get the approximate real location after the data processed by the converter.

## JZLocationConverter

The JZLocationConverter is available in both Object-C and Swift; moreover, it supports CocoaPods which is a simplest way to install frameworks when you are developing an iOS App.  Here are some interfaces in the JZLocationConverter:  

WGS-84 -> GCJ-02
When you input a coordinate outside of China, you stil gain the WGS-84
```swift
public func wgs84Togcj02(_ wgs84Point:CLLocationCoordinate2D,result:@escaping (_ gcj02Point:CLLocationCoordinate2D) -> Void)
```  

GCJ-02 -> WGS-84
This method has 1-2 meter error, it should be used with caution
```swift
public func gcj02ToWgs84(_ gcj02Point:CLLocationCoordinate2D,result:@escaping (_ wgs84Point:CLLocationCoordinate2D) -> Void)
```  

You need to load the Chinese borderline before using the converter.
```swift
func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        JZLocationConverter.start { (error) in
            if error != nil {
                print("失败")
            }else {
                print("成功")
            }
        }
        return true
    }
```  

You can use your custom borderline as well; consult <a href="https://github.com/JackZhouCn">JackZhou's github page</a> for additional information.
