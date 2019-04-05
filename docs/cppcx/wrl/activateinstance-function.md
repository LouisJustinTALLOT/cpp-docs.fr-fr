---
title: ActivateInstance (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 43aa34153f0e71dd665090243ff2288bff704404
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029078"
---
# <a name="activateinstance-function"></a>ActivateInstance (fonction)

Enregistre et récupère une instance d’un type spécifié défini dans un ID de classe spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un type à activer.

*activatableClassId*<br/>
Le nom de l’ID de classe qui définit le paramètre *T*.

*instance*<br/>
Lorsque cette opération se termine, une référence à une instance de *T*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la cause de l’erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Windows::Foundation

## <a name="see-also"></a>Voir aussi

[Windows::Foundation, espace de noms](windows-foundation-namespace.md)