---
title: /TLBID | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d651546733f42b1a714ac7a39992fa2d392c8fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839866"
---
# <a name="tlbid"></a>tlbid
**Spécifique à C++**  
  
 Permet de charger des bibliothèques autres que la bibliothèque de types principale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbid(number)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `number`  
 Numéro de la bibliothèque de types dans `filename`.  
  
## <a name="remarks"></a>Notes  
 Si plusieurs bibliothèques de types sont générées dans une même DLL, il est possible de charger des bibliothèques autres que la bibliothèque de types primaires à l'aide de `tlbid`.  
  
 Par exemple :  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 équivaut à :  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **FIN spécifique à C++**  
  
## <a name="see-also"></a>Voir aussi  
 [attributs #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directive)](../preprocessor/hash-import-directive-cpp.md)