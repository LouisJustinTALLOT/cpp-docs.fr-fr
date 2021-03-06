---
description: En savoir plus sur:/HIGHENTROPYVA
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: ae7851bb9160601ef8732120dca12132dbfdee2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200037"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Spécifie si l'image exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>Notes

Cette option modifie l’en-tête d’un fichier *image exécutable* (par exemple, un *`.dll`* *`.exe`* fichier ou) pour indiquer la prise en charge d’une adresse ASLR 64 bits. Pour avoir un effet, définissez l’option sur le fichier exécutable et tous les modules dont il dépend. Les systèmes d’exploitation qui prennent en charge l’ASLR 64 bits peuvent rebaser les segments de l’image exécutable au moment du chargement à l’aide d’adresses virtuelles 64 bits aléatoires. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, l’éditeur de liens active les **`/HIGHENTROPYVA`** images exécutables 64 bits. Cette option requiert [`/DYNAMICBASE`](dynamicbase.md) et [`/LARGEADDRESSAWARE`](largeaddressaware.md) , qui sont également activés par défaut pour les images 64 bits. **`/HIGHENTROPYVA`** n’est pas applicable aux images exécutables 32 bits, où l’option est ignorée. Pour désactiver explicitement cette option, utilisez **`/HIGHENTROPYVA:NO`** .

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)\
[`/DYNAMICBASE`](dynamicbase.md)\
[`/LARGEADDRESSAWARE`](largeaddressaware.md)\
[Défenses de la sécurité logicielle ISV Windows](/previous-versions/bb430720(v=msdn.10))
