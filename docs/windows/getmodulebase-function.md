---
title: GetModuleBase, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 40289903eba2ce7ac35d4d0b208c3b609efb09f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650812"
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