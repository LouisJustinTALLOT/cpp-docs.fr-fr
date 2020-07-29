---
title: Déclarations de variables simples
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 42547828e78566982053d22e8288fe1ccbe6e26b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229530"
---
# <a name="simple-variable-declarations"></a>Déclarations de variables simples

La déclaration d'une variable simple, la forme la plus simple d'un déclarateur direct, spécifie le nom et le type de la variable. Elle spécifie également la classe de stockage et le type de données de la variable.

Les classes de stockage ou les types (ou les deux) sont requis sur les déclarations de variables. Les variables non typées (telles que `var;`) génèrent des avertissements.

## <a name="syntax"></a>Syntaxe

*déclarateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*

*identificateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractère*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

Pour les types arithmétiques, de structure, d’Union, d’énumération et void, ainsi que pour les types représentés par des **`typedef`** noms, des déclarateurs simples peuvent être utilisés dans une déclaration dans la mesure où le spécificateur de type fournit toutes les informations de saisie. Les types de pointeur, de tableau et de fonction nécessitent des déclarateurs plus complexes.

Vous pouvez utiliser une liste d'identificateurs séparés par une virgule (**,**) pour spécifier plusieurs variables dans la même déclaration. Toutes les variables définies dans la déclaration ont le même type de base. Par exemple :

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

Les variables `x` et `y` peuvent contenir n’importe quelle valeur de l’ensemble défini par le **`int`** type pour une implémentation particulière. L'objet simple `z` est initialisé à 1 et n'est pas modifiable.

Si la déclaration de `z` concernait une variable statique non initialisée ou était dans la portée du fichier, elle recevrait la valeur initiale 0, et cette valeur ne serait pas modifiable.

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

Dans cet exemple, les variables, `reply` et `flag` , ont le **`unsigned long`** type et contiennent des valeurs intégrales non signées.

## <a name="see-also"></a>Voir aussi

[Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)
