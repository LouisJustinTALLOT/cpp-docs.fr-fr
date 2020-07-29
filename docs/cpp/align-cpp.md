---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 0a1212f1c78f49029f82be5a2f5d82ea1788b6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227658"
---
# <a name="align-c"></a>align (C++)

Dans Visual Studio 2015 et versions ultérieures, utilisez le spécificateur standard C++ 11 **`alignas`** pour contrôler l’alignement. Pour plus d’informations, consultez [alignment](../cpp/alignment-cpp-declarations.md).

**Spécifique à Microsoft**

Utilisez `__declspec(align(#))` pour contrôler avec précision l'alignement des données définies par l'utilisateur (par exemple, les allocations statiques ou les données automatiques dans une fonction).

## <a name="syntax"></a>Syntaxe

> déclarateur **__declspec (align (** *#* **))** *declarator*

## <a name="remarks"></a>Notes

L'écriture d'applications qui utilisent les dernières instructions du processeur introduit de nouvelles contraintes et de nouveaux problèmes. De nombreuses instructions nouvelles requièrent des données qui sont alignées sur des limites de 16 octets. En outre, en alignant les données fréquemment utilisées sur la taille de la ligne de cache du processeur, vous améliorez les performances du cache. Par exemple, si vous définissez une structure dont la taille est inférieure à 32 octets, vous pouvez avoir besoin d’un alignement de 32 octets pour vous assurer que les objets de ce type de structure sont mis en cache efficacement.

\#valeur d’alignement. Les entrées valides sont des puissances entières de deux comprises entre 1 et 8192 (octets), telles que 2, 4, 8, 16, 32 ou 64. `declarator`données que vous déclarez comme alignées.

Pour plus d’informations sur la façon de retourner une valeur de type `size_t` qui est la spécification d’alignement du type, consultez [`alignof`](../cpp/alignof-operator.md) . Pour plus d’informations sur la façon de déclarer des pointeurs non alignés lorsque vous ciblez des processeurs 64 bits, consultez [`__unaligned`](../cpp/unaligned.md) .

Vous pouvez utiliser `__declspec(align(#))` lorsque vous définissez un **`struct`** , un **`union`** ou un **`class`** , ou lorsque vous déclarez une variable.

Le compilateur ne garantit pas ou ne tente pas de conserver l’attribut d’alignement des données au cours d’une opération de copie ou de transformation de données. Par exemple, [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) peut copier un struct déclaré avec `__declspec(align(#))` à n’importe quel emplacement. Les allocateurs ordinaires (par exemple, [`malloc`](../c-runtime-library/reference/malloc.md) C++ [`operator new`](new-operator-cpp.md) et les allocateurs Win32) retournent généralement de la mémoire qui n’est pas suffisamment alignée pour les `__declspec(align(#))` structures ou les tableaux de structures. Pour garantir que la destination d’une opération de copie ou de transformation de données est correctement alignée, utilisez [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) . Ou, écrivez votre propre allocateur.

Vous ne pouvez pas spécifier d’alignement pour les paramètres de fonction. Lorsque vous transmettez des données qui ont un attribut d’alignement par valeur sur la pile, l’alignement est contrôlé par la Convention d’appel. Si l'alignement des données est important dans la fonction appelée, copiez le paramètre dans la mémoire correctement alignée avant de l'utiliser.

Sans `__declspec(align(#))` , le compilateur aligne généralement les données sur les frontières naturelles en fonction du processeur cible et de la taille des données, jusqu’à des limites de 4 octets sur les processeurs 32 bits et des limites de 8 octets sur les processeurs 64 bits. Les données des classes ou des structures sont alignées dans la classe ou la structure au minimum de leur alignement naturel et du paramètre de compression actuel (à partir de `#pragma pack` ou de l' `/Zp` option de compilateur).

Cet exemple illustre l'utilisation de `__declspec(align(#))` :

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Ce type a maintenant un attribut d'alignement de 32 octets. Cela signifie que toutes les instances statiques et automatiques démarrent sur une limite de 32 octets. Les types de structures supplémentaires déclarés avec ce type en tant que membre conservent l’attribut d’alignement de ce type, autrement dit, toute structure avec `Str1` comme élément a un attribut d’alignement d’au moins 32.

Ici, `sizeof(struct Str1)` est égal à 32. Cela implique que si un tableau d' `Str1` objets est créé et que la base du tableau est alignée sur 32 octets, chaque membre du tableau est également aligné sur 32 octets. Pour créer un tableau dont la base est correctement alignée en mémoire dynamique, utilisez [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) . Ou, écrivez votre propre allocateur.

La **`sizeof`** valeur de n’importe quelle structure est le décalage du membre final, plus la taille de ce membre, arrondie au multiple le plus proche de la plus grande valeur d’alignement de membre ou à la valeur d’alignement de la structure entière, selon celle qui est la plus grande.

Le compilateur utilise ces règles pour l'alignement de la structure :

- À moins d'une substitution par `__declspec(align(#))`, l'alignement d'un membre de structure scalaire représente le minimum de sa taille et de la compression actuelle.

- À moins d'une substitution par `__declspec(align(#))`, l'alignement d'une structure est la valeur maximale des alignements de ses membres.

- Un membre de structure est placé à un offset à partir du début de sa structure parente qui est le plus petit multiple de son alignement supérieur ou égal au décalage de la fin du membre précédent.

- La taille d'une structure est le plus petit multiple de son plus grand alignement supérieur ou égal au décalage de la fin de son dernier membre.

`__declspec(align(#))` peut uniquement augmenter les restrictions d'alignement.

Pour plus d'informations, consultez les pages suivantes :

- [`align`Illustre](#vclrfalignexamples)

- [Définition de nouveaux types avec`__declspec(align(#))`](#vclrf_declspecaligntypedef)

- [Alignement des données dans le stockage local des threads](#vclrfthreadlocalstorageallocation)

- [`align`Fonctionnement avec la compression des données](#vclrfhowalignworkswithdatapacking)

- [Exemples d’alignement de structure](../build/x64-software-conventions.md#examples-of-structure-alignment) (spécifique à x64)

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>Exemples d’alignement

Les exemples suivants montrent comment `__declspec(align(#))` affecte la taille et l'alignement des structures de données. Les exemples supposent les définitions suivantes :

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

Dans cet exemple, la structure `S1` est définie à l'aide de `__declspec(align(32))`. Toutes les utilisations de `S1` pour une définition de variable ou dans d'autres types de déclaration sont alignées sur 32 octets. `sizeof(struct S1)` retourne 32, et `S1` a 16 octets de remplissage après les 16 octets requis pour contenir les quatre entiers. Chaque **`int`** membre nécessite un alignement sur 4 octets, mais l’alignement de la structure elle-même est déclaré comme étant 32. L’alignement global est ensuite 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

Dans cet exemple, `sizeof(struct S2)` retourne 16, qui est exactement la somme des tailles membres, car il s’agit d’un multiple de la plus grande exigence d’alignement (un multiple de 8).

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

Dans l'exemple suivant, `sizeof(struct S3)` retourne 64.

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

Dans cet exemple, notez que `a` a l'alignement de son type naturel, dans le cas présent, 4 octets. Toutefois, `S1` doit être aligné sur 32 octets. 28 octets de remplissage suivent `a` , de sorte que `s1` commence à l’offset 32. `S4`hérite ensuite de la spécification d’alignement de `S1` , car il s’agit de la plus grande exigence d’alignement dans la structure. `sizeof(struct S4)` retourne 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
   struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Les trois déclarations de variable suivantes utilisent également `__declspec(align(#))`. Dans chaque cas, la variable doit être alignée sur 32 octets. Dans le tableau, l’adresse de base du tableau, pas chaque membre du tableau, est alignée sur 32 octets. La **`sizeof`** valeur de chaque membre du tableau n’est pas affectée lorsque vous utilisez `__declspec(align(#))` .

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Pour aligner chaque membre d'un tableau, écrivez un code tel que le suivant :

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

Dans cet exemple, notez que l'alignement de la structure elle-même et l'alignement du premier élément ont le même effet :

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` et `S7` ont les mêmes caractéristiques d'alignement, d'allocation et de taille.

Dans cet exemple, l'alignement des adresses de début a, b, c et d sont 4, 1, 4 et 1, respectivement.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Quand la mémoire est allouée sur le tas, l'alignement dépend de la fonction d'allocation appelée.  Par exemple, si vous utilisez `malloc`, le résultat dépend de la taille d’opérande. Si *arg* >= 8, la mémoire retournée est alignée sur 8 octets. Si *arg* < 8, l’alignement de la mémoire retournée est la première puissance de 2 inférieure à *arg*. Par exemple, si vous utilisez `malloc(7)` , l’alignement est de 4 octets.

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>Définition de nouveaux types avec`__declspec(align(#))`

Vous pouvez définir un type avec une caractéristique d'alignement.

Par exemple, vous pouvez définir un **`struct`** avec une valeur d’alignement de la façon suivante :

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

À présent, `aType` et `bType` sont de la même taille (8 octets) mais les variables de type `bType` sont alignées sur 32 octets.

## <a name="aligning-data-in-thread-local-storage"></a><a name="vclrfthreadlocalstorageallocation"></a>Alignement des données dans le stockage local des threads

Le stockage local des threads de type statique (TLS) créé avec l'attribut `__declspec(thread)` et placé dans la section TLS de l'image contribue à l'alignement exactement comme les données statiques normales. Pour créer des données TLS, le système d'exploitation alloue de la mémoire de la taille de la section TLS et respecte l'attribut d'alignement de la section TLS.

Cet exemple montre différentes façons de placer des données alignées dans le stockage local des threads.

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>`align`Fonctionnement avec la compression des données

L' `/Zp` option de compilateur et le `pack` pragma ont pour effet de compresser les données pour les membres de structure et d’Union. Cet exemple montre comment `/Zp` et `__declspec(align(#))` fonctionnent ensemble :

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

Le tableau suivant répertorie le décalage de chaque membre sous différentes `/Zp` valeurs (ou `#pragma pack` ), en illustrant la façon dont les deux interagissent.

|Variable|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

Pour plus d’informations, consultez [ `/Zp` (alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md).

Le décalage d'un objet est basé sur le décalage de l'objet précédent et du paramètre de compactage actif, sauf si l'objet a un attribut `__declspec(align(#))`. Dans ce cas, l'alignement est basé sur le décalage de l'objet précédent et de la valeur `__declspec(align(#))` pour l'objet.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[`__declspec`](../cpp/declspec.md)<br/>
[Vue d’ensemble des conventions ABI ARM](../build/overview-of-arm-abi-conventions.md)<br/>
[Conventions des logiciels x64](../build/x64-software-conventions.md)
