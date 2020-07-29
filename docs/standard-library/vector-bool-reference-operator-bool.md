---
title: vector&lt;bool&gt;::reference::operator bool
ms.date: 11/04/2016
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
ms.openlocfilehash: bb757fee9d6ec824a99557c409b1c4f02f48db5d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215385"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

Fournit une conversion implicite de `vector<bool>::reference` en **`bool`** .

## <a name="syntax"></a>Syntaxe

```cpp
operator bool() const;
```

## <a name="return-value"></a>Valeur de retour

Valeur booléenne de l’élément de l’objet [Vector \<bool> ](../standard-library/vector-bool-class.md) .

## <a name="remarks"></a>Notes

L'objet `vector<bool>` ne peut pas être modifié par cet opérateur.

## <a name="requirements"></a>Spécifications

**En-tête :**\<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Vector \<bool> :: Reference, classe](../standard-library/vector-bool-reference-class.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
