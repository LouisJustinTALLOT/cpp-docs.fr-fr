---
title: Initialisation des types d'agrégats
ms.date: 11/04/2016
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
ms.openlocfilehash: f6816a6f63de262b927a3c5aeed8774ba29c2eaa
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "62326077"
---
# <a name="initializing-aggregate-types"></a>Initialisation des types d'agrégats

Un type d’*agrégat* est un type de structure, d’union ou de tableau. Si un type agrégat contient des membres de types d'agrégat, les règles d'initialisation s'appliquent de manière récursive.

## <a name="syntax"></a>Syntaxe

*initialiseur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{**  *initializer-List*  **}** /* pour l’initialisation d’agrégats\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{**  *initializer-List*  **,}**

*initialiseur-List*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*initializer-List*  **,**  *initialiseur*

L'élément *initializer-list* est une liste d'initialiseurs séparés par des virgules. Chaque initialiseur de la liste est une expression constante ou une liste d'initialiseurs. Par conséquent, les listes d'initialiseurs peuvent être imbriquées. Cette forme est utile pour initialiser les membres d'agrégats d'un type d'agrégat, comme indiqué dans les exemples de cette section. Toutefois, si l'initialiseur d'un identificateur automatique est une expression unique, il n'a pas besoin d'être une expression constante ; il doit simplement avoir le type approprié pour être assigné à l'identificateur.

Pour chaque liste d'initialiseurs, les valeurs des expressions constantes sont assignées, dans l'ordre, aux membres correspondants de la variable d'agrégat.

Si l'élément *initializer-list* comporte moins de valeurs qu'un type d'agrégat, les membres ou éléments restants du type d'agrégat sont initialisés à 0. La valeur initiale d'un identificateur automatique qui n'est pas initialisé explicitement n'est pas définie. Si *initializer-list* comporte plus de valeurs qu'un type d'agrégat, une erreur se produit. Ces règles s'appliquent à chaque liste d'initialiseurs incorporée, ainsi qu'à l'agrégat dans son ensemble.

L'initialiseur d'une structure est une expression du même type, ou une liste d'initialiseurs pour ses membres placés entre accolades (**{ }**). Les membres champs de bits sans nom ne sont pas initialisés.

Lorsqu'une union est initialisée, *initializer-list* doit être une expression constante unique. La valeur de l'expression constante est assignée au premier membre de l'union.

Si un tableau a une taille inconnue, c'est le nombre d'initialiseurs qui la détermine, et son type devient complet. Il n'existe aucun moyen de spécifier la répétition d'un initialiseur en langage C, ou d'initialiser un élément au milieu d'un tableau sans fournir toutes les valeurs précédentes. Si vous avez besoin de cette opération dans votre programme, entrez la routine en langage assembleur.

Notez que le nombre d'initialiseurs peut définir la taille du tableau :

```C
int x[ ] = { 0, 1, 2 }
```

Toutefois, si vous spécifiez la taille et indiquez un nombre erroné d'initialiseurs, le compilateur génère une erreur.

**Spécifique à Microsoft**

La taille maximale d'un tableau est définie par **size_t**. Défini dans le fichier d'en-tête STDDEF.H, **size_t** est un `unsigned int` présentant la plage de 0x00000000 à 0x7CFFFFFF.

**FIN spécifique à Microsoft**

## <a name="examples"></a>Exemples

L'exemple suivant montre des initialiseurs pour un tableau.

```C
int P[4][3] =
{
    { 1, 1, 1 },
    { 2, 2, 2 },
    { 3, 3, 3,},
    { 4, 4, 4,},
};
```

Cette instruction déclare `P` en tant que tableau de quatre par trois et initialise les éléments de la première ligne à 1, les éléments de la deuxième ligne à 2, etc., jusqu'à la quatrième ligne. Notez que la liste d'initialiseurs pour les troisième et quatrième lignes contient des virgules après la dernière expression constante. La dernière liste d'initialiseurs (`{4, 4, 4,},`) est également suivie d'une virgule. Ces virgules supplémentaires sont autorisées mais ne sont pas obligatoires ; seules les virgules qui séparent les expressions constantes et celles qui séparent les listes d'initialiseurs sont obligatoires.

Si un membre d'agrégat n'a pas de liste d'initialiseurs incorporée, les valeurs sont simplement assignées, dans l'ordre, à chaque membre du sous-agrégat. Par conséquent, l'initialisation dans l'exemple précédent équivaut à ce qui suit :

```C
int P[4][3] =
{
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4
};
```

Les accolades peuvent également apparaître entre chaque initialiseur dans la liste et permettent de clarifier l'exemple ci-dessus.

Lorsque vous initialisez une variable d'agrégat, vous devez veiller à utiliser les accolades et les listes d'initialiseurs correctement. L'exemple suivant illustre l'interprétation des accolades par le compilateur de façon plus détaillée :

```C
typedef struct
{
    int n1, n2, n3;
} triplet;

triplet nlist[2][3] =
{
    { {  1, 2, 3 }, {  4, 5, 6 }, {  7, 8, 9 } },  /* Row 1 */
    { { 10,11,12 }, { 13,14,15 }, { 16,17,18 } }   /* Row 2 */
};
```

Dans cet exemple, `nlist` est déclaré en tant que tableau de structures 2-par-3, chaque structure contenant trois membres. La ligne 1 de l'initialisation assigne des valeurs à la première ligne de `nlist`, comme suit :

1. La première accolade ouvrante sur la ligne 1 indique au compilateur que l'initialisation du premier membre d'agrégat de `nlist` (c'est-à-dire `nlist[0]`) commence.

1. La deuxième accolade ouvrante indique que l'initialisation du premier membre d'agrégat de `nlist[0]` (c'est-à-dire la structure au niveau de `nlist[0][0]`) commence.

1. La première accolade fermante termine l'initialisation de la structure `nlist[0][0]` ; l'accolade ouvrante suivante commence l'initialisation de `nlist[0][1]`.

1. Le processus se poursuit jusqu'à la fin de la ligne, où l'accolade fermante termine l'initialisation de `nlist[0]`.

La ligne 2 assigne des valeurs à la deuxième ligne de `nlist` de la même façon. Notez que les ensembles externes d'accolades englobant les initialiseurs sur les lignes 1 et 2 sont obligatoires. La construction suivante, qui omet les accolades externes, générerait une erreur :

```C
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */
{
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */
};
```

Dans cette construction, la première accolade ouvrante sur la ligne 1 démarre l'initialisation de `nlist[0]`, un tableau de trois structures. Les valeurs 1, 2, et 3 sont assignées aux trois membres de la première structure. Lorsque l'accolade fermante suivante est atteinte (après la valeur 3), l'initialisation de `nlist[0]` est terminée, et les deux structures restantes du tableau de trois structures sont automatiquement initialisées à 0. De même, `{ 4,5,6 }` initialise la première structure dans la deuxième ligne de `nlist`. Les deux structures restantes de `nlist[1]` sont définies à 0. Lorsque le compilateur rencontre la liste d'initialiseurs suivante (`{ 7,8,9 }`), il tente d'initialiser `nlist[2]`. Étant donné que `nlist` ne contient que deux lignes, cette tentative génère une erreur.

Dans l'exemple suivant, les trois membres `int` de `x` sont initialisés à 1, 2 et 3, respectivement.

```C
struct list
{
    int i, j, k;
    float m[2][3];
} x = {
        1,
        2,
        3,
       {4.0, 4.0, 4.0}
      };
```

Dans la structure `list` ci-dessus, les trois éléments de la première ligne de `m` sont initialisés à 4.0 ; les éléments de la ligne restante de `m` sont initialisés à 0.0 par défaut.

```C
union
{
    char x[2][3];
    int i, j, k;
} y = { {
            {'1'},
            {'4'}
        }
      };
```

Dans cet exemple, la variable d'union `y` est initialisée. Le premier élément de l'union est un tableau, donc l'initialiseur est un initialiseur d'agrégat. La liste d'initialiseurs `{'1'}` assigne des valeurs à la première ligne du tableau. Étant donné qu'une seule valeur s'affiche dans la liste, l'élément de la première colonne est initialisé avec le caractère `1`, et les deux éléments restants de la ligne sont initialisés à 0 par défaut. De même, le premier élément de la deuxième ligne de `x` est initialisé avec le caractère `4`, et les deux éléments restants de la ligne sont initialisés à 0.

## <a name="see-also"></a>Voir aussi

[D’initialisation](../c-language/initialization.md)
