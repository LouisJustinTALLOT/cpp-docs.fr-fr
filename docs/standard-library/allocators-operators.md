---
title: '&lt;allocators&gt;, opérateurs'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416899"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt;, opérateurs

Il s’agit des fonctions d’opérateur de modèle global définies dans &lt;allocators&gt;. Pour les fonctions d’opérateur de membre de classe, consultez la documentation de la classe.

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

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
|*left*|Un des objets allocateur dont l’inégalité doit être vérifiée.|
|*right*|Un des objets allocateur dont l’inégalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si les objets allocateur ne sont pas égaux ; **false** si les objets allocateur sont égaux.

### <a name="remarks"></a>Notes

L’opérateur de modèle retourne `!(left == right)`.

## <a name="op_eq_eq"></a>  operator==

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
|*left*|Un des objets allocateur dont l’égalité doit être vérifiée.|
|*right*|Un des objets allocateur dont l’égalité doit être vérifiée.|

### <a name="return-value"></a>Valeur de retour

**true** si les objets allocateur sont égaux ; **false** si les objets allocateur ne sont pas égaux.

### <a name="remarks"></a>Notes

Cet opérateur de modèle retourne `left.equals(right)`.

## <a name="see-also"></a>Voir aussi

[\<allocators>](../standard-library/allocators-header.md)
