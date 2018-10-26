---
title: opérateur ! =, opérateur (Microsoft::WRL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator!=
dev_langs:
- C++
ms.assetid: 785435da-87a6-4454-9bce-9d288a96dc26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 946577b3309924c49c9040c5758a4c3ece0a6bfa
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065913"
---
# <a name="operator-operator-microsoftwrl"></a>operator!=, opérateur (Microsoft::WRL)

Opérateur d’inégalité pour [ComPtr](../windows/comptr-class.md) et [ComPtrRef](../windows/comptrref-class.md) objets.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);
WRL_NOTHROW bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Paramètres

*a*<br/>
Objet gauche.

*b*<br/>
Objet droit.

## <a name="return-value"></a>Valeur de retour

**true** si les objets ne sont pas égales ; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)