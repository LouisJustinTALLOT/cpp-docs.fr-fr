---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 1bfe6e7a4646be8cea622078b4d85f20f458e1c5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627330"
---
# <a name="align-c"></a>align (C++)

Dans Visual Studio 2015 et versions ultérieures, utilisez la norme C ++ 11 `alignas` spécificateur pour contrôler l’alignement. Pour plus d’informations, consultez [alignement](../cpp/alignment-cpp-declarations.md).

**Section spécifique à Microsoft**

Utilisez `__declspec(align(#))` pour contrôler avec précision l'alignement des données définies par l'utilisateur (par exemple, les allocations statiques ou les données automatiques dans une fonction).

## <a name="syntax"></a>Syntaxe

> **__declspec (align (** *#* **))** *déclarateur*

## <a name="remarks"></a>Notes

L'écriture d'applications qui utilisent les dernières instructions du processeur introduit de nouvelles contraintes et de nouveaux problèmes. En particulier, de nombreuses nouvelles instructions nécessitent que les données soient alignées sur des limites de 16 octets. En outre, en alignant fréquemment les données utilisées sur la taille de ligne de cache d'un processeur spécifique, vous améliorez la performance du cache. Par exemple, si vous définissez une structure dont la taille est inférieure à 32 octets, vous pouvez l'aligner sur 32 octets pour garantir que les objets de ce type de structure sont mis en cache efficacement.

\# est la valeur d’alignement. Les entrées valides sont des puissances entières de deux comprises entre 1 et 8192 (octets), telles que 2, 4, 8, 16, 32 ou 64. `declarator` correspond aux données que vous déclarez comme alignées.

Pour plus d’informations sur la façon de retourner une valeur de type `size_t` qui est la spécification d’alignement du type, consultez [__alignof](../cpp/alignof-operator.md). Pour plus d’informations sur la façon de déclarer des pointeurs non alignés lors du ciblage de processeurs 64 bits, consultez [__unaligned](../cpp/unaligned.md).

Vous pouvez utiliser `__declspec(align(#))` lorsque vous définissez un **struct**, **union**, ou **classe**, ou lorsque vous déclarez une variable.

Le compilateur ne garantit pas et ne tente pas de préserver l'attribut d'alignement des données durant une opération de copie ou de transformation de données. Par exemple, [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) peut copier un struct déclaré avec `__declspec(align(#))` à n’importe quel emplacement. Notez qu’ordinaire allocateurs — par exemple, [malloc](../c-runtime-library/reference/malloc.md), C++ [opérateur new](new-operator-cpp.md)et les allocateurs Win32 — retournent une mémoire qui est généralement pas suffisamment alignée pour `__declspec(align(#))` structures ou des tableaux de structures. Pour garantir que la destination d’une opération de transformation de copie ou de données est correctement alignée, utilisez [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), ou écrivez votre propre allocateur.

Vous ne pouvez pas spécifier d'alignement des paramètres de fonction. Quand des données qui ont un attribut d'alignement sont passées par valeur dans la pile, leur alignement est contrôlé par la convention d'appel. Si l'alignement des données est important dans la fonction appelée, copiez le paramètre dans la mémoire correctement alignée avant de l'utiliser.

Sans `__declspec(align(#))`, le compilateur aligne généralement les données sur les frontières naturelles en fonction du processeur cible et la taille des données, jusqu'à des limites de 4 octets sur les processeurs 32 bits et les limites de 8 octets sur les processeurs 64 bits. Les données dans les classes ou les structures sont alignées dans la classe ou la structure au minimum de leur alignement naturel et du paramètre actuel de compression (à partir du #pragma `pack` ou de l'option de compilateur `/Zp`).

Cet exemple illustre l'utilisation de `__declspec(align(#))` :

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Ce type a maintenant un attribut d'alignement de 32 octets. Cela signifie que toutes les instances statiques et automatiques commencent à une frontière de 32 octets. Autres types de structure déclarés avec ce type en tant que membre conservent l’attribut d’alignement de ce type, autrement dit, toute structure avec `Str1` comme un élément a un attribut d’alignement d’au moins 32.

Notez que `sizeof(struct Str1)` est égal à 32. Cela implique que si un tableau d'objets Str1 est créé et si la base du tableau est alignée sur 32 octets, chaque membre du tableau est également aligné sur 32 octets. Pour créer un tableau dont la base est correctement alignée en mémoire dynamique, utilisez [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), ou écrivez votre propre allocateur.

La valeur `sizeof` d'une structure quelconque est le décalage du membre final, plus la taille de ce membre, arrondie au multiple le plus proche de la plus grande valeur membre d'alignement du membre ou de la valeur d'alignement de la structure entière, quelle que soit la valeur la plus grande.

Le compilateur utilise ces règles pour l'alignement de la structure :

- À moins d'une substitution par `__declspec(align(#))`, l'alignement d'un membre de structure scalaire représente le minimum de sa taille et de la compression actuelle.

- À moins d'une substitution par `__declspec(align(#))`, l'alignement d'une structure est la valeur maximale des alignements de ses membres.

- Un membre de structure est placé dans un décalage par rapport au début de sa structure parente qui est le plus petit multiple de son alignement supérieur ou égal au décalage de la fin du membre précédent.

- La taille d'une structure est le plus petit multiple de son plus grand alignement supérieur ou égal au décalage de la fin de son dernier membre.

`__declspec(align(#))` peut uniquement augmenter les restrictions d'alignement.

Pour plus d'informations, voir :

- [Exemples d’alignement](#vclrfalignexamples)

- [Définition de nouveaux Types avec __declspec(align(#))](#vclrf_declspecaligntypedef)

- [Alignement des données dans le stockage Local des threads](#vclrfthreadlocalstorageallocation)

- [Comment aligner des travaux avec compression de données](#vclrfhowalignworkswithdatapacking)

- [Exemples d’alignement de Structure](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64 spécifique)

## <a name="vclrfalignexamples"></a> Exemples d’alignement

Les exemples suivants montrent comment `__declspec(align(#))` affecte la taille et l'alignement des structures de données. Les exemples supposent les définitions suivantes :

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

Dans cet exemple, la structure `S1` est définie à l'aide de `__declspec(align(32))`. Toutes les utilisations de `S1` pour une définition de variable ou dans d'autres types de déclaration sont alignées sur 32 octets. `sizeof(struct S1)` retourne 32, et `S1` a 16 octets de remplissage après les 16 octets requis pour contenir les quatre entiers. Chaque **int** membre nécessite un alignement de 4 octets, mais l’alignement de la structure elle-même est déclaré comme étant 32. Ainsi, l'alignement global est sur 32 octets.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

Dans cet exemple, `sizeof(struct S2)` retourne 16, qui est exactement la somme des tailles membres, car il s'agit d'un multiple de la plus grande spécification d'alignement (un multiple de 8).

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

Dans cet exemple, notez que `a` a l'alignement de son type naturel, dans le cas présent, 4 octets. Toutefois, `S1` doit être aligné sur 32 octets. Vingt-huit octets de remplissage suivent `a`, afin que `s1` démarre au décalage 32. `S4` hérite de la spécification d'alignement de `S1`, car il s'agit de la plus grande spécification d'alignement de la structure. `sizeof(struct S4)` retourne 64.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Les trois déclarations de variable suivantes utilisent également `__declspec(align(#))`. Dans chaque cas, la variable doit être alignée sur 32 octets. Pour un tableau, l'adresse de base du tableau, mais pas chaque membre du tableau, est aligné sur 32 octets. La valeur `sizeof` de chaque membre du tableau n'est pas affectée par l'utilisation de `__declspec(align(#))`.

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

Quand la mémoire est allouée sur le tas, l'alignement dépend de la fonction d'allocation appelée.  Par exemple, si vous utilisez `malloc`, le résultat dépend de la taille d’opérande. Si *arg* > = 8, la mémoire retournée est alignée de 8 octets. Si *arg* < 8, l’alignement de la mémoire retournée représente la première puissance de 2 inférieure à *arg*. Par exemple, si vous utilisez malloc (7), l'alignement est sur 4 octets.

## <a name="vclrf_declspecaligntypedef"></a> Définition de nouveaux Types avec __declspec(align(#))

Vous pouvez définir un type avec une caractéristique d'alignement.

Par exemple, vous pouvez définir un `struct` avec un valeur d’alignement de cette façon :

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Maintenant, `aType` et `bType` sont la même taille (8 octets), mais les variables de type `bType` sont alignées sur 32 octets.

## <a name="vclrfthreadlocalstorageallocation"></a> Alignement des données dans le stockage Local des threads

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

## <a name="vclrfhowalignworkswithdatapacking"></a> Comment aligner des travaux avec compression de données

Le `/Zp` option du compilateur et le `pack` pragma ont pour effet de compresser les données pour les membres de structure et d’union. Cet exemple montre comment `/Zp` et `__declspec(align(#))` fonctionnent ensemble :

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

Le tableau suivant répertorie le décalage de chaque membre pour diverses valeurs `/Zp` (ou #pragma `pack`), en indiquant leur mode d'interaction.

|Variable|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

Pour plus d’informations, consultez l’article [/Zp (Alignement des membres de la structure)](../build/reference/zp-struct-member-alignment.md).

Le décalage d'un objet est basé sur le décalage de l'objet précédent et du paramètre de compactage actif, sauf si l'objet a un attribut `__declspec(align(#))`. Dans ce cas, l'alignement est basé sur le décalage de l'objet précédent et de la valeur `__declspec(align(#))` pour l'objet.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Vue d’ensemble des conventions ABI ARM](../build/overview-of-arm-abi-conventions.md)<br/>
[x64 conventions des logiciels](../build/x64-software-conventions.md)