---
title: '&lt;allocators&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7d22e550c7054c2197163f2edf829ec17a85a145
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204558"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt;, opérateurs

Il s’agit des fonctions d’opérateur de modèle global définies dans &lt; allocators &gt; . Pour les fonctions d’opérateur de membre de classe, consultez la documentation de la classe.

|||
|-|-|
|[opérateur ! =](#op_neq)|[opérateur = =](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>opérateur ! =

Vérifie l'inégalité entre les objets allocateurs d'une classe spécifiée.

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*gauche*|Un des objets allocateur dont l’inégalité doit être vérifiée.|
|*Oui*|Un des objets allocateur dont l’inégalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**`true`** Si les objets allocateur ne sont pas égaux ; **`false`** si les objets allocateur sont égaux.

### <a name="remarks"></a>Notes

L’opérateur de modèle retourne `!(left == right)`.

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur = =

Vérifie l'égalité entre les objets allocateurs d'une classe spécifiée.

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*gauche*|Un des objets allocateur dont l’égalité doit être vérifiée.|
|*Oui*|Un des objets allocateur dont l’égalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**`true`** Si les objets allocateur sont égaux ; **`false`** si les objets allocateurs ne sont pas égaux.

### <a name="remarks"></a>Notes

Cet opérateur de modèle retourne `left.equals(right)`.

## <a name="see-also"></a>Voir aussi

[\<allocators>](allocators-header.md)
