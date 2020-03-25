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
ms.openlocfilehash: d1109e769352d412df8348822e05b66063159ee8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214225"
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

*instance*<br/>
Lorsque cette opération est terminée, une référence à une instance de *T*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la cause de l’erreur.

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Windows :: Foundation

## <a name="see-also"></a>Voir aussi

[Windows::Foundation, espace de noms](windows-foundation-namespace.md)
