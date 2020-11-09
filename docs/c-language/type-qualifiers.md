---
title: Qualificateurs de type
description: Décrit les qualificateurs de type pour le langage C utilisé dans le compilateur Microsoft Visual C
ms.date: 11/6/2020
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
ms.openlocfilehash: dd36aeb5d142eebbd6e4a339fe6c18925a6fd45a
ms.sourcegitcommit: 3f0c1dcdcce25865d1a1022bcc5b9eec79f69025
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94381608"
---
# <a name="type-qualifiers"></a>Qualificateurs de type

Les qualificateurs de type fournissent une des deux propriétés à un identificateur. Le **`const`** qualificateur de type déclare un objet comme étant non modifiable. Le **`volatile`** qualificateur de type déclare un élément dont la valeur peut légitimement être modifiée par un élément au-delà du contrôle du programme dans lequel il apparaît, par exemple un thread s’exécutant simultanément.

Les qualificateurs de type, **`const`** , **`restrict`** et **`volatile`** , ne peuvent apparaître qu’une seule fois dans une déclaration. Les qualificateurs de type peuvent apparaître avec n’importe quel spécificateur de type ; Toutefois, ils ne peuvent pas apparaître après la première virgule dans une déclaration d’élément multiple. Par exemple, les déclarations suivantes sont autorisées :

```c
typedef volatile int VI;
const int ci;
```

Les déclarations suivantes ne sont pas autorisées :

```c
typedef int *i, volatile *vi;
float f, const cf;
```

Les qualificateurs de type sont appropriés uniquement lors de l'accès à des identificateurs sous la forme d'l-values dans des expressions. Consultez [Expressions L-value et r-value](../c-language/l-value-and-r-value-expressions.md) pour plus d'informations sur les l-values et les expressions.

## <a name="syntax"></a>Syntaxe

*`type-qualifier`* :\
&emsp;**`const`**\
&emsp;**`restrict`**\
&emsp;**`volatile`**

## <a name="const-and-volatile"></a>`const` et `volatile`

Les éléments suivants sont **`const`** des **`volatile`** déclarations légales et :

```c
int const *p_ci;      // Pointer to constant int
int const (*p_ci);   // Pointer to constant int
int *const cp_i;     // Constant pointer to int
int (*const cp_i);   // Constant pointer to int
int volatile vint;     // Volatile integer
```

Si la spécification d'un type tableau inclut des qualificateurs de type, l'élément est qualifié, pas le type tableau. Si la spécification du type de fonction comprend des qualificateurs, le comportement est non défini. **`volatile`** et **`const`** n’affectent pas la plage de valeurs ou les propriétés arithmétiques de l’objet.

- Le **`const`** mot clé peut être utilisé pour modifier tout type fondamental ou d’agrégat, ou un pointeur vers un objet de tout type, ou un **`typedef`** . Si un élément est déclaré avec uniquement le **`const`** qualificateur de type, son type est considéré comme **const int**. Une **`const`** variable peut être initialisée ou placée dans une zone de stockage en lecture seule. Le **`const`** mot clé est utile pour déclarer des pointeurs vers **`const`** , car cela requiert que la fonction ne modifie pas le pointeur d’une manière ou d’une autre.

- Le compilateur suppose que, à tout moment dans le programme, une **`volatile`** variable est accessible par un processus inconnu qui utilise ou modifie sa valeur. Quelles que soient les optimisations spécifiées sur la ligne de commande, le code pour chaque assignation ou référence d’une **`volatile`** variable doit être généré même s’il semble n’avoir aucun effet.

Si **`volatile`** est utilisé seul, **`int`** est pris par défaut. Le **`volatile`** spécificateur de type peut être utilisé pour fournir un accès fiable aux emplacements de mémoire spéciaux. À utiliser **`volatile`** avec les objets de données qui peuvent être consultés ou modifiés par les gestionnaires de signaux, en exécutant simultanément des programmes ou par un matériel spécial tel que les registres de contrôle d’e/s mappées en mémoire. Vous pouvez déclarer une variable comme **`volatile`** pour sa durée de vie, ou vous pouvez effectuer un cast d’une référence unique en la valeur **`volatile`** .

- Un élément peut être à **`const`** la fois et **`volatile`** , auquel cas l’élément n’a pas pu être modifié de manière légitime par son propre programme, mais il peut être modifié par un processus asynchrone.
 
## `restrict`

Le **`restrict`** qualificateur de type, introduit dans C99, peut être appliqué aux déclarations de pointeur. Il qualifie le pointeur, pas ce qu’il pointe.

**`restrict`** est un indicateur d’optimisation pour le compilateur qu’aucun autre pointeur dans la portée actuelle ne fait référence au même emplacement de mémoire. Autrement dit, seul le pointeur ou une valeur dérivée de celui-ci (tel que le pointeur + 1) est utilisé pour accéder à l’objet pendant la durée de vie du pointeur. Cela permet au compilateur de produire du code plus optimisé. C++ a un mécanisme équivalent, [`__restrict`](../cpp/extension-restrict.md)

Gardez à l’esprit qu’il **`restrict`** s’agit d’un contrat entre vous et le compilateur. Si vous effectuez un alias d’un pointeur marqué avec **`restrict`** , le résultat n’est pas défini.

Voici un exemple qui utilise **`restrict`** :

```c
void test(int* restrict first, int* restrict second, int* val)
{
    *first += *val;
    *second += *val;
}

int main()
{
    int i = 1, j = 2, k = 3;
    test(&i, &j, &k);

    return 0;
}

// Marking union members restrict tells the compiler that
// only z.x or z.y will be accessed in any scope, which allows
// the compiler to optimize access to the members.
union z 
{
    int* restrict x;
    double* restrict y;
};
```

## <a name="see-also"></a>Voir aussi

[`/std` (Spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)\
[Déclarations et types](../c-language/declarations-and-types.md)
