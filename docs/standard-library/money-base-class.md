---
title: money_base, classe
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_base
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
ms.openlocfilehash: c614832b0cbb1cc23e42ecb3a939ccf1334a5cea
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689322"
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

- `none` pour qu’il corresponde à zéro ou plusieurs espaces ou ne génère rien.

- `sign` de correspondance ou de génération d’un signe positif ou négatif.

- `space` pour qu’il corresponde à zéro ou plusieurs espaces ou pour générer un espace.

- `symbol` pour la correspondance ou la génération d’un symbole monétaire.

- `value` pour la correspondance ou la génération d’une valeur monétaire.

## <a name="requirements"></a>spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
