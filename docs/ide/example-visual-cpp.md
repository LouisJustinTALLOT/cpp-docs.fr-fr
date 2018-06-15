---
title: '&lt;example&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- <example>
- example
dev_langs:
- C++
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cefd38a18447d0e8c9121d61c0ba963e9da39187
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33321429"
---
# <a name="ltexamplegt-visual-c"></a>&lt;example&gt; (Visual C++)
La balise \<example> vous permet de spécifier un exemple d’utilisation d’une méthode ou de tout autre membre de bibliothèque. En règle générale, cela implique également l’utilisation de la balise [\<code>](../ide/code-visual-cpp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `description`  
 Description de l’exemple de code.  
  
## <a name="remarks"></a>Notes  
 Compilez avec [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
  
```  
// xml_example_tag.cpp  
// compile with: /clr /doc /LD  
// post-build command: xdcmake xml_example_tag.dll  
  
/// Text for class MyClass.  
public ref class MyClass {  
public:  
   /// <summary>  
   /// GetZero method  
   /// </summary>  
   /// <example> This sample shows how to call the GetZero method.  
   /// <code>  
   /// int main()   
   /// {  
   ///    return GetZero();  
   /// }  
   /// </code>  
   /// </example>  
   static int GetZero() {  
      return 0;  
   }  
};  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Documentation XML](../ide/xml-documentation-visual-cpp.md)