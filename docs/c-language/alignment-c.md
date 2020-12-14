---
title: Alignement (C11)
description: Décrit l’alignement des types Microsoft Visual C
ms.date: 12/10/2020
helpviewer_keywords:
- _Alignof keyword [C]
- _Alignas keyword [C]
- memory, alignment
ms.openlocfilehash: 051987ae705f84d7d4972398f742143f14b53e2b
ms.sourcegitcommit: be469dd87453255b0e35e333712c8207b09b3dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440660"
---
# <a name="alignment-c11"></a>Alignement (C11)

L’une des fonctionnalités de bas niveau de C est la possibilité de spécifier l’alignement précis des objets en mémoire pour tirer le meilleur parti de l’architecture matérielle.

Les processeurs lisent et écrivent de la mémoire plus efficacement lorsque les données sont stockées à une adresse qui est un multiple de la taille des données. Par exemple, un entier sur 4 octets est accessible plus efficacement s’il est stocké à une adresse qui est un multiple de 4. Lorsque les données ne sont pas alignées, l’UC fait plus de travail pour accéder aux données.

Par défaut, le compilateur aligne les données en fonction de leur taille : **`char`** sur une limite de 1 octet, **`short`** sur une limite de 2 octets,, et sur une limite de 4 octets, sur une limite de 8 octets, **`int`** **`long`** **`float`** **`double`** et ainsi de suite.

En outre, en alignant les données fréquemment utilisées sur la taille de la ligne de cache du processeur, vous pouvez améliorer les performances du cache. Par exemple, si vous définissez une structure dont la taille est inférieure à 32 octets, vous pouvez avoir besoin de l’alignement sur 32 octets pour garantir que les instances de la structure sont mises en cache efficacement.

En règle générale, vous n’avez pas besoin de vous soucier de l’alignement. Le compilateur aligne généralement les données sur les limites naturelles qui sont basées sur le processeur cible et la taille des données. Les données sont alignées sur des limites allant jusqu’à 4 octets sur les processeurs 32 bits, et les limites de 8 octets sur les processeurs 64 bits. Toutefois, dans certains cas, vous pouvez améliorer les performances ou économiser la mémoire en spécifiant un alignement personnalisé pour vos structures de données.

Utilisez le mot clé C11 **`_Alignof`** pour obtenir l’alignement par défaut d’un type ou d’une variable, et **`_Alignas`** pour spécifier un alignement personnalisé pour une variable ou un type défini par l’utilisateur.

Les macros pratiques **`alignof`** et **`alignas`** , définies dans `<stdalign.h>` , sont mappées directement à **`_Alignof`** et **`_Alignas`** , respectivement. Ces macros correspondent aux mots clés utilisés dans C++. Par conséquent, l’utilisation des macros à la place des mots clés C peut s’avérer utile pour la portabilité du code si vous partagez du code entre les deux langages.

## <a name="alignas-and-_alignas-c11"></a>`alignas` et `_Alignas` (C11)

Utilisez **`alignas`** ou **`_Alignas`** pour spécifier l’alignement personnalisé d’une variable ou d’un type défini par l’utilisateur. Ils peuvent être appliqués à une structure, une Union, une énumération ou une variable.

### <a name="alignas-syntax"></a>Syntaxe de `alignas`

```c
alignas(type)
alignas(constant-expression)
_Alignas(type)
_Alignas(constant-expression)
```

### <a name="remarks"></a>Remarks

`_Alignas` ne peut pas être utilisé dans la déclaration d’un typedef, d’un champ de bits, d’une fonction, d’un paramètre de fonction ou d’un objet déclaré avec le `register` spécificateur.

Spécifiez un alignement qui est une puissance de deux comme 1, 2, 4, 8, 16, et ainsi de suite. N’utilisez pas une valeur inférieure à la taille du type.

Les structs et les unions ont un alignement égal au plus grand alignement d’un membre. Les octets de remplissage sont ajoutés dans les structs pour garantir que les exigences d’alignement des membres individuels sont respectées.

S’il existe plusieurs **`alignas`**  spécificateurs dans une déclaration (par exemple, un struct avec plusieurs membres qui ont des **`alignas`** spécificateurs différents), l’alignement du struct sera celui du plus grand.

### <a name="alignas-example"></a>`alignas` tels

Cet exemple utilise la macro pratique **`alignof`** , car elle est portable vers C++. Le comportement est le même si vous utilisez `_Alignof` .

```c
// Compile with /std:c11

#include <stdio.h>
#include <stdalign.h>

typedef struct 
{
    int value; // aligns on a 4-byte boundary. There will be 28 bytes of padding between value and alignas
    alignas(32) char alignedMemory[32]; // assuming a 32 byte friendly cache alignment
} cacheFriendly; // this struct will be 32-byte aligned because alignedMemory is 32-byte alligned and is the largest alignment specified in the struct

int main()
{
    printf("sizeof(cacheFriendly): %d\n", sizeof(cacheFriendly)); // 4 bytes for int value + 32 bytes for alignedMemory[] + padding to ensure  alignment
    printf("alignof(cacheFriendly): %d\n", alignof(cacheFriendly)); // 32 because alignedMemory[] is aligned on a 32-byte boundary

    /* output
        sizeof(cacheFriendly): 64
        alignof(cacheFriendly): 32
    */
}
```

## <a name="alignof-and-_alignof-c11"></a>`alignof` et `_Alignof` (C11)

`_Alignof` retourne l’alignement en octets du type spécifié. Elle retourne une valeur de type `size_t` .

### <a name="alignof-syntax"></a>Syntaxe de `alignof`

```cpp
alignof(type)
_Alignof(type)
```

### <a name="alignof-example"></a>`alignof` tels

Cet exemple utilise la macro pratique **`alignof`** , car elle est portable vers C++. Le comportement est le même si vous utilisez `_Alignof` .

```c
// Compile with /std:c11

#include <stdalign.h>
#include <stdio.h>

int main()
{
    size_t alignment = alignof(short);
    printf("alignof(short) = %d\n", alignment); // 2
    printf("alignof(int) = %d\n", alignof(int)); // 4
    printf("alignof(long) = %d\n", alignof(long)); // 4
    printf("alignof(float) = %d\n", alignof(float)); // 4
    printf("alignof(double) = %d\n", alignof(double)); // 8

    typedef struct
    {
        int a;
        double b;
    } test;

    printf("alignof(test) = %d\n", alignof(test)); // 8 because that is the alignment of the largest element in the structure

    /* output
        
       alignof(short) = 2
       alignof(int) = 4
       alignof(long) = 4
       alignof(float) = 4
       alignof(double) = 8
       alignof(test) = 8
    */
}
```

## <a name="requirements"></a>Configuration requise

[std : c++ 11](../build/reference/std-specify-language-standard-version.md) ou version ultérieure est requis.

SDK Windows version 10.0.20201.0 ou ultérieure. Cette version est actuellement une build Insider, que vous pouvez télécharger à partir des [Téléchargements Windows Insider Preview](https://www.microsoft.com/software-download/windowsinsiderpreviewSDK). Consultez [C11 et C17 : prise en main](https://devblogs.microsoft.com/cppblog/c11-and-c17-standard-support-arriving-in-msvc/#c11-and-c17-getting-started) pour obtenir des instructions sur l’installation et l’utilisation de ce kit de développement logiciel (SDK).

## <a name="see-also"></a>Voir aussi

[`/std` (Spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)\
[C++ `alignof` et `alignas`](../cpp/alignment-cpp-declarations.md#alignof-and-alignas)\
[Gestion de l’alignement des données par le compilateur](../cpp/alignment-cpp-declarations.md#compiler-handling-of-data-alignment)