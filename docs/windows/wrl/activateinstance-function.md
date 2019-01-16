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
ms.openlocfilehash: 4525ee74bc63a9655e7f1142fb1b2b6812d82bb6
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336078"
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

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Windows::Foundation

## <a name="see-also"></a>Voir aussi

[Windows::Foundation, espace de noms](windows-foundation-namespace.md)