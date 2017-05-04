---
title: "在 JavaScript 中處理 Windows 執行階段事件 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows 執行階段事件"
  - "Windows 執行階段事件 [JavaScript]"
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 在 JavaScript 中處理 Windows 執行階段事件
Windows 執行階段事件在 JavaScript 中的表示方式，不同於在 C\+\+ 或 .NET Framework 中的表示方式。  這些事件不是類別屬性，而會以傳遞至類別的 `addEventListener` 和 `removeEventListener` 方法的字串識別項表示。  例如，您可以透過將字串 "positionchanged" 傳遞至 `Geolocator.addEventListener` 方法，來加入 [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) 事件的事件處理常式：  
  
```javascript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 您也可以設定 `locator.onpositionchanged` 屬性。  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 在 JavaScript 中，Windows 執行階段事件引數會以單一事件物件表示。  在下列事件處理常式方法範例中，`ev` 參數是包含傳送者 \(目標屬性\) 和其他事件引數的物件。  事件引數是針對每個事件記錄的引數。  
  
```javascript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  在 Internet Explorer 中執行的應用程式無法使用 Windows 執行階段功能。  
  
## 請參閱  
 [在 JavaScript 中使用 Windows 執行階段](../jswinrt/using-the-windows-runtime-in-javascript.md)