---
title: Implements::cancastto, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 328691877a3b129c852460f8f68cdd3db4974e6f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595297"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo, méthode

Obtient un pointeur vers l’interface spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Paramètres

*riid*  
Une référence à un ID d’interface.

*PPV*  
Si réussie, un pointeur vers l’interface spécifiée par *riid*.

## <a name="return-value"></a>Valeur de retour

S_OK en cas de réussite ; Sinon, un HRESULT qui indique l’erreur, telles que E_NOINTERFACE.

## <a name="remarks"></a>Notes

Il s’agit d’une fonction d’assistance interne qui exécute une opération de QueryInterface.

## <a name="requirements"></a>Configuration requise

**En-tête :** implements.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Implements, structure](../windows/implements-structure.md)