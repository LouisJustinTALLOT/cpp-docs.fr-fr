---
title: Tailles de type et de variable dans l'assembly inline
ms.date: 08/30/2018
ms.topic: reference
f1_keywords:
- length
- Type
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
ms.openlocfilehash: 36c97ee866ca449e9bbcf514e464a13f24f12cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166891"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>Tailles de type et de variable dans l'assembly inline

**Section spécifique à Microsoft**

Le **longueur**, **taille**, et **TYPE** opérateurs ont une signification limitée dans l’assembly inline. Ils ne peuvent pas du tout être utilisés avec l'opérateur `DUP` (car vous ne pouvez pas définir des données avec des directives ou des opérateurs MASM). Toutefois, vous pouvez les utiliser pour rechercher la taille des variables ou types C ou C++ :

- Le **longueur** opérateur peut retourner le nombre d’éléments dans un tableau. Il retourne la valeur 1 pour les variables non-tableau.

- Le **taille** opérateur peut retourner la taille d’une variable C ou C++. Taille d’une variable est le produit de ses **longueur** et **TYPE**.

- Le **TYPE** opérateur peut retourner la taille d’une variable ou de type C ou C++. Si la variable est un tableau, **TYPE** retourne la taille d’un seul élément du tableau.

Par exemple, si votre programme comporte un élément de 8 **int** tableau,

```cpp
int arr[8];
```

les expressions C et d'assembly suivantes génèrent la taille d'un tableau `arr` et de ses éléments.

|__asm|C|Size|
|-------------|-------|----------|
|**LONGUEUR** arr|`sizeof`(arr)/`sizeof`(arr[0])|8|
|**TAILLE** arr|`sizeof`(arr)|32|
|**TYPE** arr|`sizeof`(arr[0])|4|

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Utilisation du langage assembleur dans les blocs __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>