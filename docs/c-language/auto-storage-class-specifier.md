---
title: Spécificateur de classe de stockage auto
ms.date: 11/04/2016
ms.assetid: 8e73f57e-aa92-4e41-91ea-5c8ad2a2b332
ms.openlocfilehash: 6bd36fd534602a5a4df95047a830058e8c5ef163
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313465"
---
# <a name="auto-storage-class-specifier"></a>Spécificateur de classe de stockage auto

Le spécificateur de classe de stockage **auto** déclare une variable automatique, une variable avec une durée de vie locale. Une variable **auto** est visible uniquement dans le bloc dans lequel elle est déclarée. Les déclarations de variables **auto** peuvent inclure des initialiseurs, comme indiqué dans [Initialisation](../c-language/initialization.md). Les variables avec la classe de stockage **auto** ne sont pas initialisées automatiquement, vous devez soit explicitement les initialiser lorsque vous les déclarez, ou leur assigner des valeurs initiales des instructions dans le bloc. Les valeurs des variables **auto** non initialisées sont éliminées. (Une variable locale **auto** ou une classe de stockage **register** est initialisée chaque fois qu'elle est dans la portée si un initialiseur est donné.)

Une variable interne **statique** (une variable statique avec une portée de bloc ou locale) peut être initialisée avec l’adresse de tout élément externe ou **statique**, mais pas avec l’adresse d’un autre élément **auto**, car l’adresse d’un élément **auto** n’est pas une constante.

## <a name="see-also"></a>Voir aussi

[Auto, mot clé](../cpp/auto-keyword.md)
