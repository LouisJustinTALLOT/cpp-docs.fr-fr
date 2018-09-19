---
title: Interprétation des déclarateurs plus complexes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- complex declarators
- interpreting complex declarators
ms.assetid: dd5b7019-c86d-4645-a5cc-21f834de6f4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6fc5b831d00c83569bc01a5580f511d126fb97bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083104"
---
# <a name="interpreting-more-complex-declarators"></a>Interprétation des déclarateurs plus complexes

Vous pouvez placer n'importe quel déclarateur entre parenthèses pour spécifier une interprétation particulière d'un « déclarateur complexe ». Un déclarateur complexe est un identificateur qualifié par plusieurs modificateurs de tableau, de pointeur ou de fonction. Vous pouvez appliquer différentes combinaisons de modificateurs de tableau, de pointeur et de fonction à un même identificateur. En général, `typedef` peut être utilisé pour simplifier les déclarations. Consultez [Déclarations typedef](../c-language/typedef-declarations.md).

Lors de l'interprétation des déclarateurs complexes, les crochets et les parenthèses (autrement dit, les modificateurs situés à droite de l'identificateur) sont prioritaires par rapport aux astérisques (autrement dit, les modificateurs situés à gauche de l'identificateur). Les crochets et les parenthèses ont la même priorité et s'associent de gauche à droite. Une fois le déclarateur interprété entièrement, le spécificateur de type est appliqué comme dernière étape. En utilisant des parenthèses, vous pouvez substituer l'ordre d'association par défaut et forcer une interprétation particulière. Toutefois, vous ne devez jamais utiliser de parenthèse autour d'un nom d'identificateur seul. Cela pourrait être interprété à tort comme une liste de paramètres.

Un moyen simple d'interpréter les déclarateurs complexes consiste à les lire « depuis l'intérieur », à l'aide des quatre étapes suivantes :

1. Commencez par l'identificateur et examinez les crochets ou les parenthèses qui figurent juste à droite (le cas échéant).

1. Interprétez ces crochets ou ces parenthèses, puis recherchez des astérisques à gauche.

1. Si vous rencontrez une parenthèse fermante à une étape quelconque, revenez en arrière et appliquez les règles 1 et 2 à tout le contenu entre parenthèses.

1. Appliquez le spécificateur de type.

    ```
    char *( *(*var)() )[10];
     ^   ^  ^ ^ ^   ^    ^
     7   6  4 2 1   3    5
    ```

Dans cet exemple, les étapes sont numérotées dans l'ordre et peuvent être interprétées comme suit :

1. L'identificateur `var` est déclaré comme

1. un pointeur vers

1. une fonction retournant

1. un pointeur vers

1. un tableau de 10 éléments, qui sont

1. des pointeurs vers

1. des valeurs `char`.

## <a name="examples"></a>Exemples

Les exemples suivants illustrent d'autres déclarations complexes et montrent comment les parenthèses peuvent affecter la signification d'une déclaration.

```
int *var[5]; /* Array of pointers to int values */
```

Le modificateur de tableau ayant une priorité plus élevée que le modificateur de pointeur, `var` est déclaré comme un tableau. Le modificateur de pointeur s'applique au type des éléments du tableau. Par conséquent, les éléments du tableau sont des pointeurs vers des valeurs `int`.

```
int (*var)[5]; /* Pointer to array of int values */
```

Dans cette déclaration pour `var`, les parenthèses donnent au modificateur de pointeur une priorité plus élevée que le modificateur de tableau et `var` est déclaré comme étant un pointeur vers un tableau de cinq valeurs `int`.

```
long *var( long, long ); /* Function returning pointer to long */
```

Les modificateurs de fonction ont également une priorité plus élevée que les modificateurs de pointeur. Par conséquent, cette déclaration pour `var` déclare `var` comme étant une fonction qui retourne un pointeur vers une valeur **long**. La fonction est déclarée comme prenant deux valeurs **long** comme arguments.

```
long (*var)( long, long ); /* Pointer to function returning long */
```

Cet exemple est semblable au précédent. Les parenthèses donnent au modificateur de pointeur une priorité plus élevée que le modificateur de fonction et `var` est déclaré comme étant un pointeur vers une fonction qui retourne une valeur **long**. Là encore, la fonction prend deux arguments **long**.

```
struct both       /* Array of pointers to functions */
{                 /*   returning structures         */
    int a;
    char b;
} ( *var[5] )( struct both, struct both );
```

Les éléments d'un tableau ne peuvent pas être des fonctions, mais cette déclaration illustre plutôt comment déclarer un tableau de pointeurs vers des fonctions. Dans cet exemple, `var` est déclaré comme étant un tableau de cinq pointeurs vers des fonctions qui retournent des structures avec deux membres. Les arguments des fonctions sont déclarés comme étant deux structures avec le même type de structure, `both`. Notez que les parenthèses qui entourent `*var[5]` sont obligatoires. Sans elles, la déclaration est une tentative non conforme de déclaration d'un tableau de fonctions, comme indiqué ci-dessous :

```
/* ILLEGAL */
struct both *var[5](struct both, struct both);
```

L'instruction suivante déclare un tableau de pointeurs.

```
unsigned int *(* const *name[5][10] ) ( void );
```

Le tableau `name` comporte 50 éléments organisés dans un tableau multidimensionnel. Les éléments sont des pointeurs vers un pointeur qui est une constante. Ce pointeur de constante pointe vers une fonction qui n'a aucun paramètre et qui retourne un pointeur vers un type non signé.

L'exemple suivant est une fonction qui retourne un pointeur vers un tableau de trois valeurs **double**.

```
double ( *var( double (*)[3] ) )[3];
```

Dans cette déclaration, une fonction retourne un pointeur vers un tableau, puisque les fonctions qui retournent des tableaux sont non conformes. Ici, `var` est déclaré comme étant une fonction qui retourne un pointeur vers un tableau de trois valeurs **double**. La fonction `var` accepte un argument. L’argument, comme la valeur de retour, est un pointeur vers un tableau de trois valeurs **double**. Le type d’argument est fourni par un *abstract-declarator* complexe. Les parenthèses autour de l’astérisque dans le type d’argument sont obligatoires ; sans elles, le type d’argument serait un tableau de trois pointeurs vers des valeurs **double**. Pour obtenir une discussion et des exemples de déclarateurs abstraits, consultez [Déclarateurs abstraits](../c-language/c-abstract-declarators.md).

```
union sign         /* Array of arrays of pointers */
{                  /* to pointers to unions       */
     int x;
     unsigned y;
} **var[5][5];
```

Comme le montre l'exemple ci-dessus, un pointeur peut pointer vers un autre pointeur et un tableau peut contenir des tableaux comme éléments. Ici, `var` est un tableau de cinq éléments. Chaque élément est un tableau de pointeurs à cinq éléments vers des pointeurs vers des unions avec deux membres.

```
union sign *(*var[5])[5]; /* Array of pointers to arrays
                             of pointers to unions        */
```

Cet exemple montre comment le positionnement des parenthèses modifie la signification de la déclaration. Dans cet exemple, `var` est un tableau de pointeurs à cinq éléments vers des tableaux de pointeurs à cinq éléments vers des unions. Pour obtenir des exemples d'utilisation de `typedef` pour éviter les déclarations complexes, consultez [Déclarations typedef](../c-language/typedef-declarations.md).

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
