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
ms.openlocfilehash: 82c83e95648eeb0fc8985777156659a2ffb876a8
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58784236"
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

*factory*<br/>
Lorsque cette opération se termine, une référence à la fabrique d’activation pour le type *T*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la raison pour laquelle cette opération a échoué.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Windows::Foundation

## <a name="see-also"></a>Voir aussi

[Windows::Foundation, espace de noms](windows-foundation-namespace.md)