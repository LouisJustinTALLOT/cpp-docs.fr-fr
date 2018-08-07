---
title: Inspectableclass, Macro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a02e20f2b87afc312c24683417f808d636c2757f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608954"
---
# <a name="inspectableclass-macro"></a>InspectableClass, macro
Définit le niveau de confiance et de nom de la classe runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
### <a name="parameters"></a>Paramètres  
 *runtimeClassName*  
 Le nom textuel complet de la classe runtime.  
  
 *trustLevel*  
 Parmi les [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) valeurs énumérées.  
  
## <a name="remarks"></a>Notes  
 Le **InspectableClass** macro peut être utilisée uniquement avec les types Windows Runtime.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [RuntimeClass, classe](../windows/runtimeclass-class.md)