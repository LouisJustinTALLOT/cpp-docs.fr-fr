---
title: Getmodulebase, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 403330097f1428ee0d7650f5931aef1621f61b11
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612599"
---
# <a name="getmodulebase-function"></a>GetModuleBase, fonction
Récupère un [ModuleBase](../windows/modulebase-class.md) pointeur qui permet d’incrémenter et décrémenter le décompte de références un [RuntimeClass](../windows/runtimeclass-class.md) objet.
  
## <a name="syntax"></a>Syntaxe
  
```cpp
inline Details::ModuleBase* GetModuleBase() throw()  
```
  
## <a name="return-value"></a>Valeur de retour
 Un pointeur vers un `ModuleBase` objet.
  
## <a name="remarks"></a>Notes
 Cette fonction est utilisée en interne pour incrémenter et décrémenter le nombre de référence d’objet.
  
 Vous pouvez utiliser cette fonction pour contrôler les nombres de références en appelant [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) et [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md).
  
## <a name="requirements"></a>Configuration requise
 **En-tête :** implements.h
  
 **Espace de noms :** Microsoft::WRL
  
## <a name="see-also"></a>Voir aussi
 [Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)