---
title: typeof va à T::typeid | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0ae9f772a68735555748e6edbeb6196f1a73d2c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164516"
---
# <a name="typeof-goes-to-ttypeid"></a>typeof va à T::typeid
Le `typeof` opérateur utilisé dans les Extensions managées pour C++ a été supplanté par le `typeid` mot clé dans Visual C++.  
  
 Dans les Extensions managées, le `__typeof()` opérateur retourne associé `Type*` de l’objet lorsqu’il est passé le nom d’un type managé. Par exemple :  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 Dans la nouvelle syntaxe, `__typeof` a été remplacé par une forme supplémentaire de `typeid` qui retourne un `Type^` lorsqu’un type managé est spécifié.  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du langage général (C + c++ / CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)