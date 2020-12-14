---
description: 'En savoir plus sur : Vector &lt; bool &gt; :: Reference :: operator bool'
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
ms.openlocfilehash: 9b12df8711664aae80d8ed85340b0852b91969ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259316"
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
