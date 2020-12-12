---
description: 'En savoir plus sur : fonction Activateinstance,'
title: ActivateInstance (fonction)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 03d7b67810ee2ab287072546b098f81f43687233
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287851"
---
# <a name="activateinstance-function"></a>ActivateInstance (fonction)

Inscrit et récupère une instance d’un type spécifié défini dans un ID de classe spécifié.

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
Type à activer.

*activatableClassId*<br/>
Nom de l’ID de classe qui définit le paramètre *T*.

*instancié*<br/>
Lorsque cette opération est terminée, une référence à une instance de *T*.

## <a name="return-value"></a>Valeur renvoyée

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la cause de l’erreur.

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Windows :: Foundation

## <a name="see-also"></a>Voir aussi

[Windows :: Foundation, espace de noms](windows-foundation-namespace.md)
