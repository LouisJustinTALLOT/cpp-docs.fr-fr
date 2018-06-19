---
title: Inspectableclass, Macro | Documents Microsoft
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
ms.openlocfilehash: 922f7f74771125aed0122c408ef902da2569e5c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873769"
---
# <a name="inspectableclass-macro"></a>InspectableClass, macro
Définit le niveau de confiance et de nom de la classe runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `runtimeClassName`  
 Nom de la classe runtime textuel complet.  
  
 `trustLevel`  
 Parmi les [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) valeurs énumérées.  
  
## <a name="remarks"></a>Notes  
 Le `InspectableClass` macro peut être utilisée uniquement avec les types Windows Runtime.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** implements.h  
  
 **Espace de noms :** Microsoft::WRL  
  
## <a name="see-also"></a>Voir aussi  
 [RuntimeClass, classe](../windows/runtimeclass-class.md)