---
title: WeakRef::operator&amp; opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 900afb73-3801-4d08-9b41-2e6a62011ccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8bb81ca1591fc398b1d0814fca918309169e82c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600982"
---
# <a name="weakrefoperatoramp-operator"></a>WeakRef::operator&amp; opérateur

Retourne un `ComPtrRef` objet qui représente l’actuel **WeakRef** objet.

## <a name="syntax"></a>Syntaxe

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()  
```

## <a name="return-value"></a>Valeur de retour

Un `ComPtrRef` objet qui représente l’actuel **WeakRef** objet.

## <a name="remarks"></a>Notes

Il s’agit d’un opérateur d’assistance interne qui n’est pas destiné à être utilisé dans votre code.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[WeakRef, classe](../windows/weakref-class.md)