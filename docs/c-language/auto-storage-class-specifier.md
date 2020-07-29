---
title: Spécificateur de classe de stockage auto
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: e39b37e2dc91dce31b6871d721875c75b8ebd629
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223757"
---
# <a name="auto-storage-class-specifier"></a>`auto`Spécificateur de classe de stockage

Le **`auto`** spécificateur de classe de stockage déclare une variable automatique, une variable avec une durée de vie locale. Une **`auto`** variable est visible uniquement dans le bloc dans lequel elle est déclarée. Les déclarations de **`auto`** variables peuvent inclure des initialiseurs, comme indiqué dans [initialisation](../c-language/initialization.md). Étant donné que les variables avec la **`auto`** classe de stockage ne sont pas initialisées automatiquement, vous devez les initialiser explicitement lorsque vous les déclarez, ou leur assigner des valeurs initiales dans des instructions au sein du bloc. Les valeurs des variables non initialisées **`auto`** ne sont pas définies. (Une variable locale de **`auto`** ou une **`register`** classe de stockage est initialisée chaque fois qu’elle est dans la portée si un initialiseur est donné.)

Une **`static`** variable interne (une variable statique avec une portée de bloc ou locale) peut être initialisée avec l’adresse d’un élément externe ou externe **`static`** , mais pas avec l’adresse d’un autre **`auto`** élément, car l’adresse d’un **`auto`** élément n’est pas une constante.

## <a name="see-also"></a>Voir aussi

[`auto`Mot](../cpp/auto-keyword.md)
