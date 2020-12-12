---
description: 'En savoir plus sur : &lt; opérateur Operator (Microsoft :: wrl)'
title: 'opérateur Operator &lt; (Microsoft :: wrl)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: 1edbb8218ef07355040bd05ab99db8f97be1cb59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330776"
---
# <a name="operatorlt-operator-microsoftwrl"></a>opérateur Operator &lt; (Microsoft :: wrl)

Détermine si l’adresse d’un objet est inférieure à une autre.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, class U>
bool operator<(const ComPtr<T>& a, const ComPtr<U>& b) throw();
template<class T, class U>
bool operator<(const Details::ComPtrRef<ComPtr<T>>& a, const Details::ComPtrRef<ComPtr<U>>& b) throw();
```

### <a name="parameters"></a>Paramètres

*un*<br/>
Objet gauche.

*b*<br/>
Objet droit.

## <a name="return-value"></a>Valeur renvoyée

**`true`** Si l’adresse d' *un* est inférieure à l’adresse de *b*; Sinon, **`false`** .

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
