---
title: Alignement (déclarations C++)
description: Comment alignement des données est défini dans modern C++.
ms.date: 05/30/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: b6e03ac2b89624a0eb6602183d4ff4bf8b518f8d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450770"
---
# <a name="alignment-c-declarations"></a>Alignement (déclarations C++)

Une des fonctionnalités de bas niveau de C++ est la possibilité de spécifier avec précision l’alignement des objets en mémoire afin d’exploiter au mieux les capacités d’une architecture matérielle spécifique. Par défaut, le compilateur aligne les membres de classe et de struct sur leur valeur de taille : `bool` et `char` sur des limites de 1 octet, `short` sur des limites de 2 octets, `int`, `long`, et `float` sur des limites de 4 octets et `long long`, `double`, et `long double` sur des limites de 8 octets. Dans la plupart des scénarios, jamais avoir à se soucier de l’alignement, car l’alignement par défaut est déjà optimal. Dans certains cas, toutefois, vous pouvez obtenir améliorations significatives des performances ou des économies de mémoire, en spécifiant un alignement personnalisé pour vos structures de données. Avant Visual Studio 2015, vous pouvez utiliser les mots clés spécifiques à Microsoft `__alignof` et `declspec(alignas)` pour spécifier un alignement supérieur à la valeur par défaut. À compter de Visual Studio 2015, vous devez utiliser les C ++ 11 mots clés standard [alignof et alignas](../cpp/alignof-and-alignas-cpp.md) pour une portabilité maximale du code. Les nouveaux mots clés se comportent de la même façon sous le capot que les extensions spécifiques à Microsoft. La documentation pour ces extensions s’applique également pour les nouveaux mots clés. Pour plus d’informations, consultez [__alignof, opérateur](../cpp/alignof-operator.md) et [aligner](../cpp/align-cpp.md). Le C++ standard ne spécifie un comportement de compression pour l’alignement sur des limites inférieures à la valeur par défaut du compilateur pour la plateforme cible, vous devez donc encore utiliser #pragma Microsoft [pack](../preprocessor/pack.md) dans ce cas.

Utilisez le [aligned_storage (classe)](../standard-library/aligned-storage-class.md) pour l’allocation de mémoire des structures de données présentant des alignements personnalisés. Le [aligned_union classe](../standard-library/aligned-union-class.md) permet de spécifier l’alignement pour les unions avec des constructeurs non triviaux ou des destructeurs.

## <a name="about-alignment"></a>Présentation de l'alignement

L'alignement est une propriété d'une adresse mémoire, exprimée sous la forme de l'adresse numérique modulo une puissance de 2. Par exemple, l’adresse 0x0001103F modulo 4 est 3. Cette adresse est considérée comme étant alignée sur 4n + 3, où 4 indique la puissance de 2 choisie. L’alignement d’une adresse dépend de la puissance de 2 choisie. La même adresse modulo 8 est 7. Une adresse est considérée comme étant alignée sur X si son alignement est Xn+0.

Processeurs exécutent des instructions qui opèrent sur les données stockées en mémoire. Les données sont identifiées par leur adresse en mémoire. Une référence unique a également une taille. Nous appelons une donnée *alignés naturellement* si son adresse est alignée à sa taille. Il est appelé *non alignés* dans le cas contraire. Par exemple, une référence à virgule flottante de 8 octets est naturellement alignée si l’adresse utilisée pour l’identifier a un alignement de 8 octets.

## <a name="compiler-handling-of-data-alignment"></a>Gestion du compilateur d’alignement des données

Compilateurs tentent d’apporter des allocations de données d’une manière qui empêche l’alignement des données.

Pour les types de données simples, le compilateur assigne des adresses qui sont des multiples de la taille en octets du type de données. Par exemple, le compilateur assigne des adresses aux variables de type `long` qui sont des multiples de 4, la définition de 2 bits de l’adresse la partie inférieure à zéro.

Le compilateur remplit également les structures de façon à aligner naturellement chaque élément de la structure. Considérez la structure `struct x_` dans l’exemple de code suivant :

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
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
}
```

1. Les deux déclarations retournent `sizeof(struct x_)` 12 octets.

1. La deuxième déclaration inclut deux éléments de remplissage :

1. `char _pad0[3]` Pour aligner le `int b` membre sur une limite de 4 octets

1. `char _pad1[1]` Pour aligner les éléments du tableau de la structure `struct _x bar[3];`

1. Le remplissage aligne les éléments de `bar[3]` d’une manière qui autorise l’accès physique.

Le code suivant montre l’exemple le `bar[3]` mise en page du tableau :

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

## <a name="see-also"></a>Voir aussi

[Alignement de structure de données](https://en.wikipedia.org/wiki/Data_structure_alignment)
