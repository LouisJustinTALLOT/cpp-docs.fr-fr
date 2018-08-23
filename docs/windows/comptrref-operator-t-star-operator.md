---
title: ComPtrRef::operator T *, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator T*
dev_langs:
- C++
helpviewer_keywords:
- operator T* operator
ms.assetid: b4f83370-0ebc-4d56-87c6-1a8ea2d0079b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54c370029b4e6fc90d1f210164de7d7ecb22f3a5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595417"
---
# <a name="comptrrefoperator-t-operator"></a>ComPtrRef::operator T*, opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
operator T*();
```

## <a name="remarks"></a>Notes

Retourne la valeur de la [ptr_](../windows/comptrrefbase-ptr-data-member.md) membre de données d’actuel **ComPtrRef** objet.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[ComPtrRef, classe](../windows/comptrref-class.md)  
[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)