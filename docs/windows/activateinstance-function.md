---
title: ActivateInstance (fonction) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
dev_langs:
- C++
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2ac6d8722bcdfed06ae97508b0ca7e5bb8ea00a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601450"
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

*T*  
Un type à activer.

*activatableClassId*  
Le nom de l’ID de classe qui définit le paramètre *T*.

*Instance*  
Lorsque cette opération se termine, une référence à une instance de *T*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, une erreur HRESULT qui indique la cause de l’erreur.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Windows::Foundation

## <a name="see-also"></a>Voir aussi

[Windows::Foundation, espace de noms](../windows/windows-foundation-namespace.md)