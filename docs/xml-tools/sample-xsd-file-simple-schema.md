---
title: "範例 XSD 檔案：簡單結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7e1dde1-b4f6-4371-add4-935b68ec77d7
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 範例 XSD 檔案：簡單結構描述
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XSD 結構描述設計工具文件中的數個範例使用下列 XSD 檔案。這個檔案是簡單的採購單結構描述。  
  
```xml  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"   
           targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"   
           elementFormDefault="qualified">  
 <xsd:element name="PurchaseOrder" type="tns:PurchaseOrderType"/>  
 <xsd:complexType name="PurchaseOrderType">  
  <xsd:sequence>  
   <xsd:element name="ShipTo" type="tns:USAddress" maxOccurs="2"/>  
   <xsd:element name="BillTo" type="tns:USAddress"/>  
  </xsd:sequence>  
  <xsd:attribute name="OrderDate" type="xsd:date"/>  
 </xsd:complexType>  
  
 <xsd:complexType name="USAddress">  
  <xsd:sequence>  
   <xsd:element name="name"   type="xsd:string"/>  
   <xsd:element name="street" type="xsd:string"/>  
   <xsd:element name="city"   type="xsd:string"/>  
   <xsd:element name="state"  type="xsd:string"/>  
   <xsd:element name="zip"    type="xsd:integer"/>  
  </xsd:sequence>  
  <xsd:attribute name="country" type="xsd:NMTOKEN" fixed="US"/>  
 </xsd:complexType>  
</xsd:schema>  
```