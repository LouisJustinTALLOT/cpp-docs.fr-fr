---
title: GetActivationFactory (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: a2581fce3c15c96317bf68de0ed918b19edd8b38
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481705"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory (fonction)

Récupère une fabrique d’activation pour le type spécifié par le paramètre de modèle.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un paramètre de modèle qui spécifie le type de la fabrique d’activation.

*activatableClassId*<br/>
Le nom de la classe de la fabrique d’activation peut produire.

*fabrique*<br/>
Lorsque cette opération se termine, une référence à la fabrique d’activation pour le type *T*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Windows::Foundation

## <a name="see-also"></a>Voir aussi

[Windows::Foundation, espace de noms](../windows/windows-foundation-namespace.md)