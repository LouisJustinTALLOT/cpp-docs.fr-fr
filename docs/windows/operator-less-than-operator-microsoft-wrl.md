---
title: opérateur&lt; ==, opérateur (Microsoft::WRL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
dev_langs:
- C++
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5d24968f4c076605a698e1af02c8e3fa3f556610
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589710"
---
# <a name="operatorlt-operator-microsoftwrl"></a>opérateur&lt; ==, opérateur (Microsoft::WRL)

Détermine si l’adresse d’un objet est inférieur à un autre.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Paramètres

*a*  
Objet gauche.

*b*  
Objet droit.

## <a name="return-value"></a>Valeur de retour

**true** si l’adresse de *un* est inférieure à l’adresse de *b*; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)