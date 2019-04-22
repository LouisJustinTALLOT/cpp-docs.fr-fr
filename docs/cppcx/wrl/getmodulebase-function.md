---
title: GetModuleBase, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784346"
---
# <a name="getmodulebase-function"></a>Getmodulebase, fonction

Récupère un [ModuleBase](modulebase-class.md) pointeur qui permet d’incrémenter et décrémenter le décompte de références un [RuntimeClass](runtimeclass-class.md) objet.

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `ModuleBase` .

## <a name="remarks"></a>Notes

Cette fonction est utilisée en interne pour incrémenter et décrémenter le nombre de référence d’objet.

Vous pouvez utiliser cette fonction pour contrôler les nombres de références en appelant [ModuleBase::IncrementObjectCount](modulebase-class.md#incrementobjectcount) et [ModuleBase::DecrementObjectCount](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::wrl

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)