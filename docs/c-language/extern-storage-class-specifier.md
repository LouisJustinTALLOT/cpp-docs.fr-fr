---
description: 'En savoir plus sur : extern Storage-Class, spécificateur'
title: Spécificateur extern de classe de stockage
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: f3a4a583f21809761878a060a3131a000f57915f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196306"
---
# <a name="extern-storage-class-specifier"></a>Spécificateur extern de classe de stockage

Une variable déclarée avec le **`extern`** spécificateur de classe de stockage est une référence à une variable du même nom définie dans un autre fichier source. Elle permet de rendre la définition de variable au niveau externe visible. Une variable déclarée comme n' **`extern`** a aucun stockage alloué pour elle-même ; il s’agit uniquement d’un nom.

## <a name="example"></a>Exemple

Cet exemple montre les déclarations aux niveaux interne et externe :

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

Dans cet exemple, la variable `i` est définie dans Source1.c avec la valeur initiale 1. Une **`extern`** déclaration dans source2. c rend « i » visible dans ce fichier.

Dans la `func` fonction, l’adresse de la variable globale `i` est utilisée pour initialiser la **`static`** variable pointeur `external_i` . Cela fonctionne, car la variable globale a une **`static`** durée de vie, ce qui signifie que son adresse ne change pas pendant l’exécution du programme. Ensuite, une variable `i` est définie dans la portée de `func` comme une variable locale avec la valeur initiale 16. Cette définition n'affecte pas la valeur de `i` au niveau externe, qui est masquée par l'utilisation de son nom pour la variable locale. La valeur du `i` global n’est désormais accessible qu’avec le pointeur `external_i`.

## <a name="see-also"></a>Voir aussi

[Spécificateurs de classe de stockage pour les déclarations de Internal-Level](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
