---
title: ComPtr::operator ! =, opérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator!=
dev_langs:
- C++
ms.assetid: 63647240-dec7-4eb9-9272-96c07d01493c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4874121f22daa8e4a13bf7a1d332c9b8e3db60ba
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42578105"
---
# <a name="comptroperator-operator"></a>ComPtr::operator!=, opérateur

Indique si deux **ComPtr** objets ne sont pas égaux.

## <a name="syntax"></a>Syntaxe

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Paramètres

*a*  
Une référence à un **ComPtr** objet.

*b*  
Une référence à un autre **ComPtr** objet.

## <a name="return-value"></a>Valeur de retour

Le premier produit opérateur **true** si objet *un* n’est pas égal à l’objet *b*; sinon, **false**.

Les deuxième et troisième opérateurs yield **true** si objet *un* n’est pas égal à **nullptr**; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)  
[ComPtr, classe](../windows/comptr-class.md)