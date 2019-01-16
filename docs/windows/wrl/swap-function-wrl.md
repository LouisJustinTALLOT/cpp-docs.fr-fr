---
title: Swap, fonction (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: cdac008bb352bfdb7689ed7a90a5f5c522e75c88
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335963"
---
# <a name="swap-function-wrl"></a>Swap, fonction (WRL)

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Le premier argument.

*right*<br/>
Le deuxième argument.

## <a name="return-value"></a>Valeur de retour

## <a name="remarks"></a>Notes

Échange les valeurs des deux arguments spécifiés.

## <a name="requirements"></a>Spécifications

**En-tête :** internal.h

**Espace de noms :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](microsoft-wrl-details-namespace.md)