---
title: AsWeak (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: 0c3250b18422f64e71d8e8d7dac8dc5ab204145b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50616734"
---
# <a name="asweak-function"></a>AsWeak (fonction)

Récupère une référence faible à une instance spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un pointeur vers le type de paramètre *p*.

*p*<br/>
Une instance d’un type.

*pWeak*<br/>
Lorsque cette opération se termine, un pointeur vers une référence faible au paramètre *p*.

## <a name="return-value"></a>Valeur de retour

S_OK, si cette opération est réussie ; Sinon, une erreur HRESULT qui indique la cause de l’échec.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)