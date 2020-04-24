---
title: Types de classe anonymes
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: e227f48588c3c4f59c0d0bd28ab16178de159b58
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032081"
---
# <a name="anonymous-class-types"></a>Types de classe anonymes

Les cours peuvent être anonymes — c’est-à-dire qu’ils peuvent être déclarés sans *identifiant.* Ceci est utile lorsque vous remplacez un nom de classe par un nom **dactylographe,** comme dans ce qui suit:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
> L'utilisation de classes anonymes indiquée dans l'exemple précédent est utile pour conserver la compatibilité avec un code C existant. Dans certains codes C, l’utilisation de **typedef** en conjonction avec des structures anonymes est répandue.

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

Dans le code `iValue` précédent, peut être consulté à l’aide de l’opérateur de sélection des membres objet (**. .**) comme suit :

```cpp
int i = ptv.iValue;
```

Les classes anonymes sont soumises à certaines restrictions. (Pour plus d’informations sur les syndicats anonymes, voir [syndicats](../cpp/unions.md).) Cours anonymes:

- Ne peut pas avoir de constructeur ou de destructeur.

- Impossible de passer comme arguments aux fonctions (sauf si la vérification de type est rejetée à l’aide d’ellipsis).

- Ne peut pas être retourné comme valeurs de retour à partir des fonctions.

## <a name="anonymous-structs"></a>Structs anonymes

**Microsoft Spécifique**

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

**END Microsoft Spécifique**
