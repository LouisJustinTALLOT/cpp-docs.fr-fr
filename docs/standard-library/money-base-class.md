---
title: money_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: 5b19635cf4d2cce58ec50226c463a075cfac5b0f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455568"
---
# <a name="moneybase-class"></a>money_base, classe

Cette classe décrit une énumération et une structure communes à toutes les spécialisations de la classe de modèle [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Notes

L’énumération `part` décrit les valeurs possibles dans les éléments du champ de tableau dans le modèle de structure. Les valeurs de `part` sont les suivantes:

- `none`pour faire correspondre zéro, un ou plusieurs espaces ou générer Nothing.

- `sign`pour faire correspondre ou générer un signe positif ou négatif.

- `space`pour faire correspondre zéro, un ou plusieurs espaces ou générer un espace.

- `symbol`pour faire correspondre ou générer un symbole monétaire.

- `value`pour faire correspondre ou générer une valeur monétaire.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
