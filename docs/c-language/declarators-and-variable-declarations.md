---
description: 'En savoir plus sur : déclarateurs et déclarations de variable'
title: Déclarateurs et déclarations de variable
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 920c44e3345c6143489815de55ea81470e46d279
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306415"
---
# <a name="declarators-and-variable-declarations"></a>Déclarateurs et déclarations de variable

Le reste de cette section décrit la forme et la signification des déclarations pour les types de variable répertoriés dans cette liste. Plus particulièrement, les sections restantes expliquent comment déclarer les éléments suivants :

|Type de variable|Description|
|----------------------|-----------------|
|[Variables simples](../c-language/simple-variable-declarations.md)|Variables à valeur unique avec type intégral ou virgule flottante|
|[Tableaux](../c-language/array-declarations.md)|Variables composées d’une collection d’éléments du même type|
|[Pointeurs](../c-language/pointer-declarations.md)|Variables qui pointent vers d'autres variables et contiennent des emplacements de variables (sous la forme d'adresses) au lieu de valeurs|
|[Variables d’énumération](../c-language/c-enumeration-declarations.md)|Variables simples avec type intégral qui contiennent une valeur d'un ensemble de constantes entières désignées|
|[Structures](../c-language/structure-declarations.md)|Variables composées d’une collection de valeurs qui peuvent avoir des types différents|
|[Unions](../c-language/union-declarations.md)|Variables composées de plusieurs valeurs de types différents qui occupent le même espace de stockage|

Un déclarateur est la partie d'une déclaration qui spécifie le nom qui doit être introduit dans le programme. Il peut inclure des modificateurs tels que <strong>\*</strong> (pointeur vers) et l’un des mots clés de convention d’appel Microsoft.

**Spécifique à Microsoft**

Dans le déclarateur

```C
__declspec(thread) char *var;
```

**`char`** est le spécificateur de type, `__declspec(thread)` et `*` sont les modificateurs, et `var` est le nom de l’identificateur.

**FIN spécifique à Microsoft**

Vous utilisez des déclarateurs pour déclarer des tableaux de valeurs, des pointeurs vers des valeurs et des fonctions qui retournent des valeurs d'un type spécifié. Les déclarateurs sont indiqués dans le tableau et les déclarations de pointeur sont décrites plus loin dans cette section.

## <a name="syntax"></a>Syntaxe

*déclarateur*:<br/>
&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identificateur*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *déclarateur*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constante-expression*<sub>OPT</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *Parameter-type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-List*<sub>OPT</sub> **)**

*pointeur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*type-qualifier-List*<sub>OPT</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*type-qualifier-List-*<sub></sub> *pointeur* opt

*type-qualifier-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*qualificateur de type*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list type-qualifier*

> [!NOTE]
> Consultez la syntaxe des *déclarations* dans la section [Vue d’ensemble des déclarations](../c-language/overview-of-declarations.md) ou [Résumé de syntaxe du langage C](../c-language/c-language-syntax-summary.md) pour la syntaxe qui référence un *déclarateur*.

Lorsqu'un déclarateur se compose d'un identificateur non modifié, l'élément déclaré a un type de base. Si un astérisque ( <strong>\*</strong> ) apparaît à gauche d’un identificateur, le type est remplacé par un type pointeur. Si l’identificateur est suivi de crochets (**[ ]**), le type est remplacé par un type tableau. Si l'identificateur est suivi de parenthèses, le type est remplacé par un type fonction. Pour plus d’informations sur l’interprétation de la priorité dans les déclarations, consultez [Interprétation de déclarateurs plus complexes](../c-language/interpreting-more-complex-declarators.md).

Chaque déclarateur déclare au moins un identificateur. Un déclarateur doit contenir un spécificateur de type afin que la déclaration soit complète. Le spécificateur de type indique le type des éléments d’un type tableau, le type d’objet adressé par un type pointeur ou le type de retour d’une fonction.

Les déclarations de [tableau](../c-language/array-declarations.md) et de [pointeur](../c-language/pointer-declarations.md) sont décrites plus en détail plus loin dans cette section. Les exemples suivants illustrent des formes simples de déclarateurs :

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Spécifique à Microsoft**

Le compilateur Microsoft C ne limite pas le nombre de déclarateurs pouvant modifier un type arithmétique, structure ou union. Le nombre est limité uniquement par la mémoire disponible.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
