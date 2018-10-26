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
ms.openlocfilehash: afa76ad23c509689dd693bb0f3e13dbb7adb4d54
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075448"
---
# <a name="getmodulebase-function"></a>GetModuleBase, fonction
Récupère un [ModuleBase](../windows/modulebase-class.md) pointeur qui permet d’incrémenter et décrémenter le décompte de références un [RuntimeClass](../windows/runtimeclass-class.md) objet.

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `ModuleBase` .

## <a name="remarks"></a>Notes

Cette fonction est utilisée en interne pour incrémenter et décrémenter le nombre de référence d’objet.

Vous pouvez utiliser cette fonction pour contrôler les nombres de références en appelant [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) et [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)