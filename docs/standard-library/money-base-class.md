---
title: money_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: b0c77b523dbe31bc5b07ae3d736441880fe04546
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610443"
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

L’énumération `part` décrit les valeurs possibles dans les éléments du champ de tableau dans le modèle de structure. Les valeurs de `part` sont :

- `none` Pour faire correspondre zéro ou plusieurs espaces ou ne rien générer.

- `sign` Pour faire correspondre ou générer un signe positif ou négatif.

- `space` Pour faire correspondre zéro ou plusieurs espaces ou générer un espace.

- `symbol` Pour faire correspondre ou générer un symbole monétaire.

- `value` Pour faire correspondre ou générer une valeur monétaire.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
