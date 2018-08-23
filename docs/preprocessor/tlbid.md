---
title: TLBID | Microsoft Docs
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
ms.openlocfilehash: 1ec0150e63209728cf2f02c854fe03702b8a45b4
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540796"
---
# <a name="tlbid"></a>tlbid
**Spécifique à C++**  
  
Permet de charger des bibliothèques autres que la bibliothèque de types principale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tlbid(number)  
```  
  
### <a name="parameters"></a>Paramètres  
*Nombre*  
Numéro de la bibliothèque de types dans `filename`.  
  
## <a name="remarks"></a>Notes  
 
Si plusieurs bibliothèques de types sont intégrées à une même DLL, il est possible de charger des bibliothèques autres que la bibliothèque de type principal à l’aide de **tlbid**.  
  
Exemple :  
  
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
[directive #import](../preprocessor/hash-import-directive-cpp.md)