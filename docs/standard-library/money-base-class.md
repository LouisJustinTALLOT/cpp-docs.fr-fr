---
title: money_base, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_base
dev_langs:
- C++
helpviewer_keywords:
- money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 805045e4ea63f153e9a35b0d4b068bd69874b93f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864084"
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

L’énumération **part** décrit les valeurs possibles dans les éléments du champ de tableau dans le modèle de structure. Les valeurs de **part** sont les suivantes :

- **none** pour faire correspondre zéro, un ou plusieurs espaces ou pour ne rien générer.

- **sign** pour faire correspondre ou générer un signe positif ou négatif.

- **space** pour faire correspondre zéro, un ou plusieurs espaces ou pour générer un espace.

- **symbol** pour faire correspondre ou générer un symbole monétaire.

- **value** pour faire correspondre ou générer une valeur monétaire.

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
