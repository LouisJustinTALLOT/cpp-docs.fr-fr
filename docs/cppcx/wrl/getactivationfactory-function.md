---
description: 'En savoir plus sur : fonction GetActivationFactory'
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
ms.openlocfilehash: ae2384e0620282723c6f10090a0028347408b271
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97124629"
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
Paramètre de modèle qui spécifie le type de la fabrique d’activation.

*activatableClassId*<br/>
Nom de la classe que la fabrique d’activation peut produire.

*usine*<br/>
Lorsque cette opération est terminée, une référence à la fabrique d’activation pour le type *T*.

## <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la raison de l’échec de cette opération.

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Windows :: Foundation

## <a name="see-also"></a>Voir aussi

[Windows :: Foundation, espace de noms](windows-foundation-namespace.md)
