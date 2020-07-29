---
title: Types de classe anonymes
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: 77f0a5517cee5e4baeacbbdcae47bdeea2853a97
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216633"
---
# <a name="anonymous-class-types"></a>Types de classe anonymes

Les classes peuvent être anonymes, c’est-à-dire qu’elles peuvent être déclarées sans *identificateur*. Cela est utile lorsque vous remplacez un nom de classe par un **`typedef`** nom, comme suit :

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
> L'utilisation de classes anonymes indiquée dans l'exemple précédent est utile pour conserver la compatibilité avec un code C existant. Dans du code C, l’utilisation de conjointement **`typedef`** avec les structures anonymes est courante.

Les classes anonymes sont également utiles lorsque vous souhaitez qu'une référence à un membre de classe apparaisse comme si elle n'était pas été contenue dans une classe distincte, comme dans l'exemple suivant :

```cpp
struct PTValue
{
    POINT ptLoc;
    union
    {
        int  iValue;
        long lValue;
    };
};

PTValue ptv;
```

Dans le code précédent, est `iValue` accessible à l’aide de l’opérateur de sélection de membres d’objet (**.**) comme suit :

```cpp
int i = ptv.iValue;
```

Les classes anonymes sont soumises à certaines restrictions. (Pour plus d’informations sur les unions anonymes, consultez [unions](../cpp/unions.md).) Classes anonymes :

- Ne peut pas avoir de constructeur ou de destructeur.

- Ne peuvent pas être passés comme arguments à Functions (à moins que la vérification de type soit invalidée avec des points de suspension).

- Ne peut pas être retourné comme valeurs de retour à partir des fonctions.

## <a name="anonymous-structs"></a>Structs anonymes

**Spécifique à Microsoft**

Une extension Microsoft C vous permet de déclarer une variable de structure dans une autre structure sans lui donner un nom. Ces structures imbriquées sont appelées des structures anonymes. C++ n'autorise pas les structures anonymes.

Vous pouvez accéder aux membres d'une structure anonyme comme s'ils étaient des membres de la structure conteneur.

```cpp
// anonymous_structures.c
#include <stdio.h>

struct phone
{
    int  areacode;
    long number;
};

struct person
{
    char   name[30];
    char   gender;
    int    age;
    int    weight;
    struct phone;    // Anonymous structure; no name needed
} Jim;

int main()
{
    Jim.number = 1234567;
    printf_s("%d\n", Jim.number);
}
//Output: 1234567
```

**FIN spécifique à Microsoft**
