---
title: '&lt;allocators&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: 7bc37e98ed85582cac8fc7ae21e54a6d5da9e06f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364966"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt;, opérateurs

Ce sont les fonctions globales d’opérateur de modèle définies dans &lt;les allocataires.&gt; Pour les fonctions d’opérateur de membre de la classe, consultez la documentation de la classe.

|||
|-|-|
|[opérateur!](#op_neq)|[opérateur](#op_eq_eq)|

## <a name="operator"></a><a name="op_neq"></a>opérateur!

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
|*Gauche*|Un des objets allocateur dont l’inégalité doit être vérifiée.|
|*Oui*|Un des objets allocateur dont l’inégalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si les objets allocateur ne sont pas égaux ; **false** si les objets allocateur sont égaux.

### <a name="remarks"></a>Notes

L’opérateur de modèle retourne `!(left == right)`.

## <a name="operator"></a><a name="op_eq_eq"></a>opérateur

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
|*Gauche*|Un des objets allocateur dont l’égalité doit être vérifiée.|
|*Oui*|Un des objets allocateur dont l’égalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si les objets allocateur sont égaux ; **false** si les objets allocateur ne sont pas égaux.

### <a name="remarks"></a>Notes

Cet opérateur de modèle retourne `left.equals(right)`.

## <a name="see-also"></a>Voir aussi

[\<les allocataires>](../standard-library/allocators-header.md)
