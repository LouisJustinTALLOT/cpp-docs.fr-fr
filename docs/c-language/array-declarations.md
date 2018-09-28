---
title: Déclarations de tableau | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d776adab3404bf1244c7365e905866b4d041fc00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091907"
---
# <a name="array-declarations"></a>Déclarations de tableau

Une « déclaration de tableau » nomme le tableau et spécifie le type de ses éléments. Elle peut également définir le nombre d'éléments du tableau. Une variable de type tableau est considérée comme un pointeur vers le type des éléments du tableau.

## <a name="syntax"></a>Syntaxe

*declaration* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*init-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

*declarator* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator* : /\*Déclarateur de fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**

Étant donné que *constant-expression* est facultatif, la syntaxe a deux formes :

- La première forme définit une variable tableau. L’argument *constant-expression* entre crochets spécifie le nombre d’éléments du tableau. Si *constant-expression* est présent, il doit être de type intégral et sa valeur doit être supérieure à zéro. Le type de chaque élément est donné par *type-specifier*. Il peut s'agir de n'importe quel type, à l'exception de `void`. Un élément de tableau ne peut pas être un type de fonction.

- La deuxième forme déclare une variable définie ailleurs. L’argument *constant-expression* entre crochets est omis, mais pas les crochets. Vous pouvez utiliser cette forme uniquement si vous avez précédemment initialisé le tableau, si vous l'avez déclaré comme paramètre ou si vous l'avez déclaré comme référence à un tableau explicitement défini ailleurs dans le programme.

Dans les deux formes, *direct-declarator* nomme la variable et peut modifier le type de la variable. Les crochets (**[ ]**) qui suivent *direct-declarator* modifient le déclarateur en type tableau.

Des qualificateurs de type peuvent apparaître dans la déclaration d'un objet de type tableau, mais les qualificateurs s'appliquent aux éléments plutôt qu'au tableau lui-même.

Vous pouvez déclarer un tableau de tableaux (tableau « multidimensionnel ») en indiquant après le déclarateur de tableau une liste d'expressions constantes entre crochets, comme illustré ici :

> *type-specifier* *declarator* **[** *constant-expression* **]** **[** *constant-expression* **]** ...

Chaque *constant-expression* entre crochets définit le nombre d'éléments d'une dimension donnée : les tableaux à deux dimensions comportent deux expressions entre crochets, les tableaux à trois dimensions en comportent trois, et ainsi de suite. Vous pouvez omettre la première expression constante si vous avez initialisé le tableau, si vous l'avez déclaré comme paramètre ou si vous l'avez déclaré comme référence à un tableau explicitement défini ailleurs dans le programme.

Vous pouvez définir des tableaux de pointeurs en différents types d'objets en utilisant des déclarateurs complexes, comme décrit dans la section [Interprétation de déclarateurs plus complexes](../c-language/interpreting-more-complex-declarators.md).

Les tableaux sont stockés par ligne. Par exemple, le tableau suivant comprend deux lignes comportant chacune trois colonnes :

```C
char A[2][3];
```

Les trois colonnes de la première ligne sont stockées en premier, suivies des trois colonnes de la deuxième ligne. Cela signifie que le dernier indice varie plus rapidement.

Pour faire référence à un élément individuel d'un tableau, utilisez une expression d'indice, comme décrit dans la section [Opérateurs suffixés](../c-language/postfix-operators.md).

## <a name="examples"></a>Exemples

Les exemples suivants illustrent des déclarations de tableau :

```C
float matrix[10][15];
```

Le tableau à deux dimensions nommé `matrix` possède 150 éléments. Chaque élément est de type **float**.

```C
struct {
    float x, y;
} complex[100];
```

Il s'agit d'une déclaration d'un tableau de structures. Ce tableau contient 100 éléments. Chaque élément est une structure contenant deux membres.

```C
extern char *name[];
```

Cette instruction déclare le type et le nom d'un tableau de pointeurs vers `char`. La définition réelle de `name` se produit ailleurs.

**Section spécifique à Microsoft**

Le type d'entier requis pour conserver la taille maximale d'un tableau est la taille de **size_t**. Défini dans le fichier d'en-tête STDDEF.H, **size_t** est un `unsigned int` présentant la plage de 0x00000000 à 0x7CFFFFFF.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)