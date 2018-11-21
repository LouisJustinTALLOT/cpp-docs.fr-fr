---
title: Exemples d'alignement de structure
ms.date: 11/19/2018
helpviewer_keywords:
- structure alignment
- examples [C++], structure alignment
ms.assetid: 03d137bf-5cc4-472e-9583-6498f2534199
ms.openlocfilehash: 7c4b3ae29674e9c4fc27e8e175867339001b9a0d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175338"
---
# <a name="examples-of-structure-alignment"></a>Exemples d'alignement de structure

Les quatre exemples ci-dessous chaque déclarent qu'une aligné structure ou union et les chiffres correspondantes illustrent la disposition de cette structure ou union en mémoire. Chaque colonne dans une illustration représente un octet de mémoire et le numéro dans la colonne indique le décalage de cet octet. Le nom de la deuxième ligne de chaque chiffre correspond au nom d’une variable dans la déclaration. Les colonnes grisées indiquent le remplissage requis pour obtenir l’alignement spécifié.

## <a name="example-1"></a>Exemple 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Disposition de structure de l’exemple 1 de conversion AMD](../build/media/vcamd_conv_ex_1_block.png "AMD conversion exemple 1 structure de disposition")

## <a name="example-2"></a>Exemple 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Disposition de structure de l’exemple 2 de conversion AMD](../build/media/vcamd_conv_ex_2_block.png "disposition de structure de l’exemple 2 de conversion AMD")

## <a name="example-3"></a>Exemple 3

```C
// Total size = 22 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Disposition de structure de l’exemple 2 de conversion AMD](../build/media/vcamd_conv_ex_3_block.png "disposition de structure de l’exemple 2 de conversion AMD")

## <a name="example-4"></a>Exemple 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![AMD conversion exemple 4 union layouit](../build/media/vcamd_conv_ex_4_block.png "layouit union des exemple 4 conversion AMD")

## <a name="see-also"></a>Voir aussi

[Types et stockage](../build/types-and-storage.md)<br/>
