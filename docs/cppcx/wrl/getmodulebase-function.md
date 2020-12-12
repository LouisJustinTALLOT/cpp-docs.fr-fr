---
description: 'En savoir plus sur : fonction Getmodulebase,'
title: GetModuleBase, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: cdedaf905da194400209840b6bd84fa8e626eb0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295196"
---
# <a name="getmodulebase-function"></a>GetModuleBase, fonction

Récupère un pointeur [ModuleBase](modulebase-class.md) qui autorise l’incrémentation et la décrémentation du décompte de références d’un objet [RuntimeClass](runtimeclass-class.md) .

## <a name="syntax"></a>Syntaxe

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `ModuleBase`.

## <a name="remarks"></a>Notes

Cette fonction est utilisée en interne pour incrémenter et décrémenter le nombre de références d’objets.

Vous pouvez utiliser cette fonction pour contrôler le nombre de références en appelant [ModuleBase :: incrementobjectcount,](modulebase-class.md#incrementobjectcount) et [ModuleBase ::D ecrementobjectcount](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Spécifications

**En-tête :** Implements. h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
