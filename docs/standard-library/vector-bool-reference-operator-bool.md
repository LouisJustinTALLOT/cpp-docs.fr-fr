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
ms.openlocfilehash: ca2d21a7706248cd84ca3591eb717e4081972f9c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452122"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

Fournit une conversion implicite `vector<bool>::reference` de en **bool**.

## <a name="syntax"></a>Syntaxe

```cpp
operator bool() const;
```

## <a name="return-value"></a>Valeur de retour

La valeur booléenne de l’élément de l’objet [vector\<bool>](../standard-library/vector-bool-class.md).

## <a name="remarks"></a>Notes

L'objet `vector<bool>` ne peut pas être modifié par cet opérateur.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[vector\<bool>::reference, classe](../standard-library/vector-bool-reference-class.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
