---
title: 'opérateur Operator &lt; (Microsoft :: wrl)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator<
ms.assetid: bfae0e1c-1648-482b-99c2-3217d62aba46
ms.openlocfilehash: b438f823814e21e2da43f698471d782c88626628
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226878"
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

*p*<br/>
Objet droit.

## <a name="return-value"></a>Valeur de retour

**`true`** Si l’adresse d' *un* est inférieure à l’adresse de *b*; Sinon, **`false`** .

## <a name="requirements"></a>Spécifications

**En-tête :** client.h

**Espace de noms :** Microsoft::WRL

## <a name="see-also"></a>Voir aussi

[Microsoft :: WRL, espace de noms](microsoft-wrl-namespace.md)
