---
title: opérateur&lt; ==, opérateur (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 2c45f4b2c905fe925cdb52520180d83a4c156b53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645060"
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

*a*<br/>
Objet gauche.

*b*<br/>
Objet droit.

## <a name="return-value"></a>Valeur de retour

**true** si l’adresse de *un* est inférieure à l’adresse de *b*; sinon, **false**.

## <a name="requirements"></a>Configuration requise

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft::WRL, espace de noms](../windows/microsoft-wrl-namespace.md)