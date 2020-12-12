---
description: 'En savoir plus sur : `auto` spécificateur de Storage-Class'
title: Spécificateur de classe de stockage auto
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: a20e599ca7189548f92a78ff378e3b5f9f202b3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97279859"
---
# <a name="auto-storage-class-specifier"></a>`auto` Spécificateur de Storage-Class

Le **`auto`** spécificateur de classe de stockage déclare une variable automatique, une variable avec une durée de vie locale. Une **`auto`** variable est visible uniquement dans le bloc dans lequel elle est déclarée. Les déclarations de **`auto`** variables peuvent inclure des initialiseurs, comme indiqué dans [initialisation](../c-language/initialization.md). Étant donné que les variables avec la **`auto`** classe de stockage ne sont pas initialisées automatiquement, vous devez les initialiser explicitement lorsque vous les déclarez, ou leur assigner des valeurs initiales dans des instructions au sein du bloc. Les valeurs des variables non initialisées **`auto`** ne sont pas définies. (Une variable locale de **`auto`** ou une **`register`** classe de stockage est initialisée chaque fois qu’elle est dans la portée si un initialiseur est donné.)

Une **`static`** variable interne (une variable statique avec une portée de bloc ou locale) peut être initialisée avec l’adresse d’un élément externe ou externe **`static`** , mais pas avec l’adresse d’un autre **`auto`** élément, car l’adresse d’un **`auto`** élément n’est pas une constante.

## <a name="see-also"></a>Voir aussi

[`auto` Mot](../cpp/auto-cpp.md)
