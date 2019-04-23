---
title: '#If, #elif #else et #endif Directives (C/C++)'
ms.date: 11/04/2016
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
ms.openlocfilehash: 90fbab45c6408c30198c2a52a42545718002cc11
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59028089"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>Directives #if, #elif, #else et #endif (C/C++)

Le **#if** directive, avec le **#elif**, **#else**, et **#endif** directives de compilation de contrôles de certaines parties d’un fichier source. Si l’expression que vous écrivez (après le **#if**) a une valeur différente de zéro, le groupe de la ligne qui suit immédiatement la **#if** directive est conservée dans l’unité de traduction.

## <a name="grammar"></a>Grammaire

*conditionnel* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*If-partie elif-parts*<sub>opt</sub> *partie « else »*<sub>opt</sub> *endif en ligne*

*If-partie* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*texte de la ligne d’if*

*If-line* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if**  *constant-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef**  *identifier*

*elif-parts* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-line text*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*elif-parts elif-texte*

*elif-ligne* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif**  *constant-expression*

*partie « else »* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*else-line text*

*ligne Else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*ligne endif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

Chaque **#if** directive dans un fichier source doit correspondre à une fermeture **#endif** directive. Un nombre quelconque de **#elif** directives peuvent apparaître entre les **#if** et **#endif** directives, mais au plus une **#else** directive est autorisée. Le **#else** directive, le cas échéant, doit être la dernière directive avant **#endif**.

Le **#if**, **#elif**, **#else**, et **#endif** peuvent imbriquer des directives dans les parties de texte des autres **#if**directives. Chaque imbriqués **#else**, **#elif**, ou **#endif** directive appartient à la précédente la plus proche **#if** directive.

Toutes les directives de compilation conditionnelle, tel que **#if** et **#ifdef**, doit correspondre à la fermeture **#endif** directives avant la fin du fichier ; sinon, une erreur message est généré. Lorsque les directives de compilation conditionnelle sont contenues dans les fichiers include, elles doivent satisfaire aux mêmes conditions : Il ne doit y avoir aucune directive de compilation conditionnelle sans correspondance à la fin du fichier include.

Remplacement de macro est effectué dans la partie de la ligne de commande qui suit une **#elif** commande, donc un appel de macro peut être utilisé dans le *expression constante*.

Le préprocesseur sélectionne l’une des occurrences données de *texte* pour un traitement ultérieur. Un bloc spécifié dans *texte* peut être n’importe quelle séquence de texte. Il peut occuper plusieurs lignes. Généralement *texte* est le texte de programme qui a une signification pour le compilateur ou le préprocesseur.

Le préprocesseur traite le texte sélectionné *texte* et le transmet au compilateur. Si *texte* contient des directives de préprocesseur, le préprocesseur exécute ces directives. Seuls les blocs de texte sélectionnés par le préprocesseur sont compilés.

Le préprocesseur sélectionne un seul *texte* élément en évaluant l’expression constante suit chaque **#if** ou **#elif** directive jusqu'à ce qu’il trouve une constante (différent de zéro) true expression. Il sélectionne tout le texte (y compris les autres directives de préprocesseur compter **#**) jusqu'à son associé **#elif**, **#else**, ou **#endif** .

Si toutes les occurrences de *expression constante* ont la valeur false, ou si aucun **#elif** directives apparaissent, le préprocesseur sélectionne le bloc de texte après le **#else** clause. Si le **#else** clause est omise et toutes les instances de *expression constante* dans le **#if** bloc ont la valeur false, aucun bloc de texte n’est sélectionné.

Le *expression constante* est une expression constante entière avec les restrictions supplémentaires :

- Les expressions doivent avoir un type intégral et peut inclure uniquement des constantes entières, des constantes de caractère et le **défini** opérateur.

- L'expression ne peut pas utiliser `sizeof` ou un opérateur de cast de type.

- Il se peut que l'environnement cible ne puisse pas représenter toutes les plages d'entiers.

- La traduction représente le type **int** du même type que **long**, et **unsigned int** identique **unsigned long**.

- Le traducteur peut traduire les constantes caractère en un ensemble de valeurs de code différentes de l'ensemble de l'environnement cible. Pour déterminer les propriétés de l'environnement cible, vérifiez les valeurs des macros de LIMITS.H dans une application développée pour l'environnement cible.

- L'expression ne doit effectuer aucune interrogation de l'environnement et doit rester isolée par rapport aux détails d'implémentation sur l'ordinateur cible.

## <a name="defined"></a>définir

L’opérateur de préprocesseur **défini** peut être utilisé dans les expressions constantes spéciales, comme indiqué par la syntaxe suivante :

defined( `identifier` )

defined `identifier`

Cette expression constante est considéré comme true (différent de zéro) si le *identificateur* est actuellement défini ; sinon, la condition est false (0). Un identificateur défini comme du texte vide est considéré comme défini. Le **défini** directive peut être utilisée dans un **#if** et un **#elif** directive mais nulle part ailleurs.

Dans l’exemple suivant, le **#if** et **#endif** directives contrôlent la compilation d’un des trois appels de fonction :

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

L'appel de fonction à `credit` est compilé si l'identificateur `CREDIT` est défini. Si l'identificateur `DEBIT` est défini, l'appel de fonction à `debit` est compilé. Si aucun de ces deux identificateurs n'est défini, l'appel de `printerror` est compilé. Notez que `CREDIT` et `credit` sont des identificateurs distincts en C et C++, car leurs casses sont différentes.

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

La première **#if** bloc montre deux ensembles d’imbriquée **#if**, **#else**, et **#endif** directives. Le premier jeu de directives est traité uniquement si `DLEVEL > 5` a la valeur true. Sinon, les instructions situées après **#else** sont traités.

Le **#elif** et **#else** directives dans le deuxième exemple sont utilisés pour rendre une des quatre options, selon la valeur de `DLEVEL`. La constante `STACK` a la valeur 0, 100 ou 200, selon la définition de `DLEVEL`. Si `DLEVEL` est supérieur à 5, l'instruction

```C
#elif DLEVEL > 5
display(debugptr);
```

est compilée et `STACK` n'est pas défini.

Une utilisation courante de la compilation conditionnelle consiste à empêcher plusieurs inclusions du même fichier d'en-tête. En C++, où les classes sont souvent définies dans des fichiers d'en-tête, des constructions telles que les suivantes peuvent être utilisées pour empêcher plusieurs définitions :

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
...
};

#endif // !defined( EXAMPLE_H )
```

Le code précédent vérifie si la constante symbolique `EXAMPLE_H` est définie. Si oui, le fichier a déjà été inclus et il est inutile de le retraiter. Sinon, la constante `EXAMPLE_H` est définie pour marquer EXAMPLE.H comme déjà traité.

## <a name="hasinclude"></a>__has_include

**Visual Studio 2017 15.3 et versions ultérieures :**  Détermine si un en-tête de bibliothèque est disponible pour être inclus :

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