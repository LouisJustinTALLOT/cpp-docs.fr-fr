---
title: '#if, #elif, #else et #endif, directives (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: 2b7ed4733dcafda793b9a945c3f40739b52e040a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220338"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>directives #if, #elif, #else et #endif (C/C++)

La directive **#if** , avec les directives **#elif**, **#else**et **#endif** , contrôle la compilation des parties d’un fichier source. Si l’expression que vous écrivez (après le **#if**) a une valeur différente de zéro, le groupe de lignes qui suit immédiatement la directive **#if** est conservé dans l’unité de traduction.

## <a name="grammar"></a>Grammaire

*Conditional* : \
&nbsp;&nbsp;&nbsp;&nbsp;*If-part Elif-parties* <sub>OPT</sub> *autre partie* <sub>OPT</sub> *endif-ligne*

*If-part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*texte if-Line*

*If-Line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *constant-expression*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identificateur*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identifier*

*Elif-parties* : \
&nbsp;&nbsp;&nbsp;&nbsp;*texte de ligne Elif*\
&nbsp;&nbsp;&nbsp;&nbsp;*Elif-parties Elif-texte de ligne*

*Elif-ligne* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif**  *constant-expression*

*else-part* : \
&nbsp;&nbsp;&nbsp;&nbsp;*texte de ligne Else*

*else-ligne* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-ligne* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

## <a name="remarks"></a>Notes

Chaque **#if** directive d’un fichier source doit être mise en correspondance par une directive de **#endif** de fermeture. N’importe quel nombre de directives **#elif** peut apparaître entre les directives **#if** et **#endif** , mais au plus une directive **#else** est autorisée. La directive **#else** , le cas échéant, doit être la dernière directive avant **#endif**.

Les directives **#if**, **#elif**, **#else**et **#endif** peuvent être imbriquées dans les parties de *texte* d’autres directives de **#if** . Chaque directive **#else**, **#elif**ou **#endif** imbriquée appartient à la directive **#if** précédente la plus proche.

Toutes les directives de compilation conditionnelle, telles que **#if** et **#ifdef**, doivent correspondre à une directive de **#endif** de fermeture avant la fin du fichier. Dans le cas contraire, un message d’erreur est généré. Lorsque les directives de compilation conditionnelle sont contenues dans des fichiers include, elles doivent satisfaire aux mêmes conditions: Il ne doit pas y avoir de directives de compilation conditionnelle sans correspondance à la fin du fichier include.

Le remplacement de macro est effectué dans la partie de la ligne qui suit une commande **#elif** , de sorte qu’un appel de macro peut être utilisé dans l' *expression constante*.

Le préprocesseur sélectionne l’une des occurrences de *texte* données pour un traitement ultérieur. Un bloc spécifié dans le *texte* peut être n’importe quelle séquence de texte. Il peut occuper plusieurs lignes. Généralement, le *texte* est un texte de programme qui a une signification pour le compilateur ou le préprocesseur.

Le préprocesseur traite le *texte* sélectionné et le transmet au compilateur. Si le *texte* contient des directives de préprocesseur, le préprocesseur exécute ces directives. Seuls les blocs de texte sélectionnés par le préprocesseur sont compilés.

Le préprocesseur sélectionne un seul élément de *texte* en évaluant l’expression constante qui suit chaque **#if** ou **#elif** directive jusqu’à ce qu’il trouve une expression constante vraie (différente de zéro). Il sélectionne tout le texte (y compris les autres directives **#** de préprocesseur commençant par) jusqu’à son **#elif**, **#else**ou **#endif**associé.

Si toutes les occurrences de *constant-expression* ont la valeur false, ou si aucune directive **#elif** n’apparaît, le préprocesseur sélectionne le bloc de texte après la clause **#else** . Lorsqu’il n’existe aucune clause **#else** , et que toutes les instances de *constant-expression* dans le bloc **#if** ont la valeur false, aucun bloc de texte n’est sélectionné.

L' *expression constante* est une expression constante entière avec les restrictions supplémentaires suivantes:

- Les expressions doivent avoir un type intégral et ne peuvent inclure que des constantes entières, des constantes caractère et l’opérateur **défini** .

- L’expression ne peut `sizeof` pas utiliser ou un opérateur de cast de type.

- L’environnement cible peut ne pas être en mesure de représenter toutes les plages d’entiers.

- La traduction représente le type **int** de la même façon que le type **long**et unsigned **int** de la même façon que unsigned **long**.

- Le traducteur peut traduire les constantes caractère en un ensemble de valeurs de code différentes de l'ensemble de l'environnement cible. Pour déterminer les propriétés de l’environnement cible, utilisez une application générée pour cet environnement afin de vérifier les valeurs des *limites.* Macros H.

- L’expression ne doit pas interroger l’environnement et doit rester isolée des détails d’implémentation sur l’ordinateur cible.

## <a name="preprocessor-operators"></a>Opérateurs de préprocesseur

### <a name="defined"></a>définir

L’opérateur de préprocesseur **défini** peut être utilisé dans des expressions constantes spéciales, comme indiqué dans la syntaxe suivante:

> **defined (** *identificateur* **)** \
> **défini** *identificateur*

Cette expression constante est considérée comme vraie (différente de zéro) si l' *identificateur* est actuellement défini. Sinon, la condition n'est pas vérifiée (0). Un identificateur défini comme du texte vide est considéré comme défini. L’opérateur **défini** peut être utilisé dans une **#if** et une directive **#elif** , mais nulle part ailleurs.

Dans l’exemple suivant, les directives **#if** et **#endif** contrôlent la compilation de l’un des trois appels de fonction:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

L'appel de fonction à `credit` est compilé si l'identificateur `CREDIT` est défini. Si l'identificateur `DEBIT` est défini, l'appel de fonction à `debit` est compilé. Si aucun de ces deux identificateurs n'est défini, l'appel de `printerror` est compilé. Et `CREDIT` sont`credit` tous deux des identificateurs distincts en C++ C et parce que leurs cas sont différents.

Les instructions de compilation conditionnelle dans l'exemple suivant supposent une constante symbolique définie au préalable et nommée `DLEVEL`.

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

Le premier bloc **#if** montre deux ensembles de directives **#if**, **#else**et **#endif** imbriquées. Le premier jeu de directives est traité uniquement si `DLEVEL > 5` a la valeur true. Sinon, les instructions situées après **#else** sont traitées.

Les directives **#elif** et **#else** dans le deuxième exemple sont utilisées pour effectuer l’un des quatre choix, en fonction de la `DLEVEL`valeur de. La constante `STACK` a la valeur 0, 100 ou 200, selon la définition de `DLEVEL`. Si `DLEVEL` est supérieur à 5, l'instruction

```C
#elif DLEVEL > 5
display(debugptr);
```

est compilé et `STACK` n’est pas défini.

Une utilisation courante de la compilation conditionnelle consiste à empêcher plusieurs inclusions du même fichier d'en-tête. Dans C++, où les classes sont souvent définies dans les fichiers d’en-tête, les constructions comme celle-ci peuvent être utilisées pour empêcher plusieurs définitions:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

Le code précédent vérifie si la constante symbolique `EXAMPLE_H` est définie. Dans ce cas, le fichier a déjà été inclus et n’a pas besoin d’être retraité. Sinon, la constante `EXAMPLE_H` est définie pour marquer EXAMPLE.H comme déjà traité.

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 15.3 et versions ultérieures :**  Détermine si un en-tête de bibliothèque peut être inclus:

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)
