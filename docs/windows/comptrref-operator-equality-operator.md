---
title: ComPtrRef::operator ==, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator==
dev_langs:
- C++
ms.assetid: 95fcf781-b473-4317-88cd-e938778d3c3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: abf78644f7cad90d25d365f6237407aeaeb6917b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42575701"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator==, opérateur

Prend en charge l’infrastructure WRL et n’est pas destinée à être utilisée directement depuis votre code.

## <a name="syntax"></a>Syntaxe

```cpp
bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Paramètres

*a*  
Une référence à un **ComPtrRef** objet.

*b*  
Une référence à un autre **ComPtrRef** objet, ou un pointeur vers un type anonyme (`void*`).

## <a name="return-value"></a>Valeur de retour

Le premier produit opérateur **true** si objet *un* est égal à l’objet *b*; sinon, **false**.

Les deuxième et troisième opérateurs yield **true** si objet *un* est égal à **nullptr**; sinon, **false**.

Les quatrième et cinquième opérateurs yield **true** si objet *un* est égal à l’objet *b*; sinon, **false**.

## <a name="remarks"></a>Notes

Indique si deux **ComPtrRef** objets sont égaux.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Namespace :** Microsoft::WRL::Details

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL::Details, espace de noms](../windows/microsoft-wrl-details-namespace.md)  
[ComPtrRef, classe](../windows/comptrref-class.md)