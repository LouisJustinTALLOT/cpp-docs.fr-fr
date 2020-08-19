---
title: '&lt;allocators&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 2d2f928ab3773ed8e0b0afdc0113db2ef5b2a3dd
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561216"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt;, opérateurs

Il s’agit des fonctions d’opérateur de modèle global définies dans &lt; allocators &gt; . Pour les fonctions d’opérateur de membre de classe, consultez la documentation de la classe.

|||
|-|-|
|[opérateur ! =](#op_neq)|[opérateur = =](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a> opérateur ! =

Vérifie l'inégalité entre les objets allocateurs d'une classe spécifiée.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Un des objets allocateur dont l’inégalité doit être vérifiée.

*Oui*\
Un des objets allocateur dont l’inégalité doit être vérifiée.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les objets allocateur ne sont pas égaux ; **`false`** si les objets allocateur sont égaux.

### <a name="remarks"></a>Notes

L’opérateur de modèle retourne `!(left == right)`.

## <a name="operator"></a><a name="op_eq_eq"></a> opérateur = =

Vérifie l'égalité entre les objets allocateurs d'une classe spécifiée.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Un des objets allocateur dont l’égalité doit être vérifiée.

*Oui*\
Un des objets allocateur dont l’égalité doit être vérifiée.

### <a name="return-value"></a>Valeur de retour

**`true`** Si les objets allocateur sont égaux ; **`false`** si les objets allocateurs ne sont pas égaux.

### <a name="remarks"></a>Notes

Cet opérateur de modèle retourne `left.equals(right)`.

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
