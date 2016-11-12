---
title: "&#39;ParamArray&#39; cannot be applied to the first parameter of an extension method | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36554"
  - "bc36554"
helpviewer_keywords: 
  - "BC36554"
ms.assetid: 0778a854-246f-4c2b-943d-ea8883b3aa6f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# &#39;ParamArray&#39; cannot be applied to the first parameter of an extension method
'ParamArray' cannot be applied to the first parameter of an extension method. The first parameter specifies which type to extend.  
  
 The first parameter of an extension method specifies the data type that the method extends. Therefore, the first parameter is required and cannot be optional. Because a parameter array is automatically optional, it is not valid as the first argument of an extension method.  
  
> [!NOTE]
>  When the method is executed, the instance of the extended data type that invokes the method becomes the argument for the first parameter of the method. For example, the instance `greeting` in `greeting.Print()` is the argument for the first parameter, `str`, in extension method `Public Sub Print (ByVal str As String)`.  
  
 **Error ID:** BC36554  
  
### To correct this error  
  
-   If the parameter array does not specify the data type you want to extend, add a new first parameter that specifies this type.  
  
    ```  
    <Extension()>  
    Public Sub AddTo(ByRef str As String, ByVal ParamArray addOns() As String)  
    ' Concatenate the strings in addOns to str.  
    End Sub  
    ```  
  
-   If the parameter array does specify the data type you want to extend, consider changing it to a regular array, requiring an argument, instead of a parameter array. Regular arrays can be extended.  
  
    ```  
    <Extension()>  
    Public Function Sum(ByVal ints() As Integer) As Integer  
        Dim total As Integer = 0  
        For Each i As Integer In ints  
            total = total + i  
        Next i  
        Return total  
    End Function  
    ```  
  
## See Also  
 [Extension Methods](/dotnet/visual-basic/language-reference/procedures/extension-methods)   
 [Parameter Arrays](/dotnet/visual-basic/language-reference/procedures/parameter-arrays)   
 [Optional Parameters](/dotnet/visual-basic/language-reference/procedures/optional-parameters)