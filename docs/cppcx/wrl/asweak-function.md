---
title: AsWeak, fonction
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: d11f55d57f4053fd6d46b727a8ed91b340d1764b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214173"
---
# <a name="asweak-function"></a>AsWeak, fonction

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
Pointeur vers le type de paramètre *p*.

*p*<br/>
Instance d’un type.

*pWeak*<br/>
Lorsque cette opération est terminée, il s’agit d’un pointeur vers une référence faible au paramètre *p*.

## <a name="return-value"></a>Valeur de retour

S_OK, si cette opération réussit ; Sinon, une erreur HRESULT qui indique la cause de l’échec.

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](microsoft-wrl-namespace.md)
