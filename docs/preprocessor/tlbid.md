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
ms.openlocfilehash: f5bd922089bcf189c403a97679a593a985603a12
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446255"
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
 
[attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directive #import](../preprocessor/hash-import-directive-cpp.md)