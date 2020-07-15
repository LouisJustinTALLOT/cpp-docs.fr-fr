---
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: b2ff9929de74d99fbc45e4f4ff38fd6b939697bc
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373825"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Spécifie si l'image exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **/HIGHENTROPYVA**[**: no**]

## <a name="remarks"></a>Notes

Cette option modifie l’en-tête d’une *image exécutable*, un fichier. dll ou. exe pour indiquer si l’ASLR avec des adresses 64 bits est pris en charge. Quand cette option est définie au niveau d’un fichier exécutable et de tous les modules dont il dépend, un système d’exploitation qui prend en charge l’ASLR 64 bits peut redéfinir les segments de l’image exécutable au moment du chargement en utilisant des adresses aléatoires tirées d’un espace d’adressage virtuel de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, l’éditeur de liens active **/HIGHENTROPYVA** pour les images exécutables 64 bits. Cette option requiert [/LARGEADDRESSAWARE](largeaddressaware.md), qui est également activée par défaut pour les images 64 bits. **/HIGHENTROPYVA** n’est pas applicable aux images exécutables 32 bits, où l’option est ignorée. Pour désactiver explicitement cette option, utilisez **/HIGHENTROPYVA : no**. Pour que cette option ait un effet, l’option [/DynamicBase](dynamicbase.md) doit également être définie.

## <a name="see-also"></a>Voir aussi

- [Options EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Défenses de la sécurité logicielle ISV Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
