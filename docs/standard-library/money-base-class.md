---
description: 'En savoir plus sur : classe money_base'
title: money_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: 295984cfed4d6fdd47c772e29765c1484f52d32a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230469"
---
# <a name="money_base-class"></a>money_base, classe

La classe décrit une énumération et une structure commune à toutes les spécialisations du modèle de classe [moneypunct](../standard-library/moneypunct-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};
```

## <a name="remarks"></a>Notes

L’énumération `part` décrit les valeurs possibles dans les éléments du champ de tableau dans le modèle de structure. Les valeurs de `part` sont les suivantes :

- `none` pour faire correspondre zéro, un ou plusieurs espaces ou générer Nothing.

- `sign` pour faire correspondre ou générer un signe positif ou négatif.

- `space` pour faire correspondre zéro, un ou plusieurs espaces ou générer un espace.

- `symbol` pour faire correspondre ou générer un symbole monétaire.

- `value` pour faire correspondre ou générer une valeur monétaire.

## <a name="requirements"></a>Spécifications

**En-tête :**\<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
