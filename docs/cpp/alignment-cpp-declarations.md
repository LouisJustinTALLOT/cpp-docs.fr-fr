---
title: Alignment
description: Comment l’alignement des données est spécifié C++dans moderne.
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 45b22742394a0b1c159e8b8102a26802a2441929
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076113"
---
# <a name="alignment"></a>Alignment

Une des fonctionnalités de bas niveau de C++ est la possibilité de spécifier avec précision l’alignement des objets en mémoire afin d’exploiter au mieux les capacités d’une architecture matérielle spécifique. Par défaut, le compilateur aligne les membres de classe et de struct sur leur valeur de taille : `bool` et `char` sur des limites de 1 octet, `short` sur les limites de 2 octets, `int`, `long`et `float` sur des limites de 4 octets, et `long long`, `double`et `long double` sur des limites de 8 octets.

Dans la plupart des scénarios, vous n’avez pas à vous soucier de l’alignement, car l’alignement par défaut est déjà optimal. Toutefois, dans certains cas, vous pouvez obtenir des améliorations significatives en matière de performances, ou économiser de la mémoire, en spécifiant un alignement personnalisé pour vos structures de données. Avant Visual Studio 2015, vous pouviez utiliser les mots clés spécifiques à Microsoft `__alignof` et `declspec(alignas)` pour spécifier un alignement supérieur à la valeur par défaut. À compter de Visual Studio 2015, vous devez utiliser les mots clés standard C++ 11 **alignof** et **alignas** pour une portabilité maximale du code. Les nouveaux mots clés se comportent de la même façon que les extensions spécifiques à Microsoft. La documentation de ces extensions s’applique également aux nouveaux mots clés. Pour plus d’informations, consultez [__Alignof Operator](../cpp/alignof-operator.md) et [align](../cpp/align-cpp.md). La C++ norme ne spécifie pas le comportement de compression pour l’alignement sur les limites inférieures à la valeur par défaut du compilateur pour la plateforme cible. vous devez donc toujours utiliser Microsoft #pragma [Pack](../preprocessor/pack.md) dans ce cas.

Utilisez la [classe aligned_storage](../standard-library/aligned-storage-class.md) pour l’allocation de mémoire des structures de données avec des alignements personnalisés. La [classe aligned_union](../standard-library/aligned-union-class.md) est destinée à spécifier l’alignement des unions avec des constructeurs ou des destructeurs non triviales.

## <a name="alignment-and-memory-addresses"></a>Alignement et adresses mémoire

L'alignement est une propriété d'une adresse mémoire, exprimée sous la forme de l'adresse numérique modulo une puissance de 2. Par exemple, l’adresse 0x0001103F modulo 4 est 3. Cette adresse est dite alignée sur 4n + 3, où 4 indique la puissance de 2 choisie. L’alignement d’une adresse dépend de la puissance de 2 choisie. La même adresse modulo 8 est 7. Une adresse est considérée comme étant alignée sur X si son alignement est Xn+0.

Les processeurs exécutent des instructions qui fonctionnent sur les données stockées en mémoire. Les données sont identifiées par leurs adresses en mémoire. Une seule donnée a également une taille. Nous appelons une référence *naturellement alignée* si son adresse est alignée sur sa taille. Sinon, il est appelé *mal aligné* . Par exemple, une référence à virgule flottante de 8 octets est naturellement alignée si l’adresse utilisée pour l’identifier a un alignement sur 8 octets.

## <a name="compiler-handling-of-data-alignment"></a>Gestion de l’alignement des données par le compilateur

Les compilateurs tentent d’effectuer des allocations de données d’une manière qui empêche l’alignement des données.

Pour les types de données simples, le compilateur assigne des adresses qui sont des multiples de la taille en octets du type de données. Par exemple, le compilateur assigne des adresses aux variables de type `long` qui sont des multiples de 4, en définissant les 2 bits inférieurs de l’adresse à zéro.

Le compilateur remplit également les structures d’une manière qui aligne naturellement chaque élément de la structure. Considérez la structure `struct x_` dans l’exemple de code suivant :

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

Le compilateur remplit cette structure pour appliquer naturellement l'alignement.

L’exemple de code suivant montre comment le compilateur place la structure remplie dans la mémoire :

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

Les deux déclarations retournent `sizeof(struct x_)` sous la forme de 12 octets.

La deuxième déclaration inclut deux éléments de remplissage :

1. `char _pad0[3]` d’aligner le membre `int b` sur une limite de 4 octets.

1. `char _pad1[1]` pour aligner les éléments de tableau de la structure `struct _x bar[3];` sur une limite de 4 octets.

Le remplissage aligne les éléments de `bar[3]` d’une manière qui autorise l’accès naturel.

L’exemple de code suivant montre la disposition de tableau `bar[3]` :

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="alignof-and-alignas"></a>alignof et alignas

Le spécificateur de type **alignas** est un moyen portable C++ et standard de spécifier l’alignement personnalisé des variables et des types définis par l’utilisateur. L’opérateur **alignof** est également un moyen portable standard d’obtenir l’alignement d’un type ou d’une variable spécifiés.

## <a name="example"></a>Exemple

Vous pouvez utiliser **aligneras** sur une classe, un struct ou une Union, ou sur des membres individuels. Quand plusieurs spécificateurs **alignas** sont rencontrés, le compilateur choisit le plus strict, (celui ayant la plus grande valeur).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Voir aussi

[Alignement de la structure des données](https://en.wikipedia.org/wiki/Data_structure_alignment)
