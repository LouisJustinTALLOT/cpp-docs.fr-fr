---
description: En savoir plus sur les tailles de type et de variable dans l’assembly inline
title: Tailles de type et de variable dans l'assembly inline
ms.date: 08/30/2018
ms.topic: reference
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: 0d6822537f542c159c40c0ed6f14dca93aa36525
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122016"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Tailles de type et de variable dans l'assembly inline

**Spécifique à Microsoft**

Les opérateurs de **longueur**, de **taille** et de **type** ont une signification limitée dans l’assembly inline. Ils ne peuvent pas du tout être utilisés avec l'opérateur `DUP` (car vous ne pouvez pas définir des données avec des directives ou des opérateurs MASM). Toutefois, vous pouvez les utiliser pour rechercher la taille des variables ou types C ou C++ :

- L’opérateur de **longueur** peut retourner le nombre d’éléments d’un tableau. Il retourne la valeur 1 pour les variables non-tableau.

- L’opérateur **Size** peut retourner la taille d’une variable C ou C++. La taille d’une variable est le produit de sa **longueur** et de son **type**.

- L’opérateur de **type** peut retourner la taille d’un type ou d’une variable C ou C++. Si la variable est un tableau, **type** retourne la taille d’un élément unique du tableau.

Par exemple, si votre programme comporte un tableau à 8 éléments **`int`** ,

```cpp
int arr[8];
```

les expressions C et d'assembly suivantes génèrent la taille d'un tableau `arr` et de ses éléments.

|__asm|C|Taille|
|-------------|-------|----------|
|**Longueur** arr|`sizeof(arr)/sizeof(arr[0])`|8|
|**Taille** arr|`sizeof(arr)`|32|
|**Tapez** arr|`sizeof(arr[0])`|4|

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
