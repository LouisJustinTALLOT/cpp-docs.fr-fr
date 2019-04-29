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
ms.openlocfilehash: 90d3c868eaab85e3b1a2a416c9aa14b0e27ec8f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270222"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Spécifie si l'image exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>Notes

Cette option modifie l’en-tête d’un *image exécutable*, un fichier .dll ou .exe, pour indiquer si ASLR avec des adresses 64 bits est pris en charge. Quand cette option est définie au niveau d’un fichier exécutable et de tous les modules dont il dépend, un système d’exploitation qui prend en charge l’ASLR 64 bits peut redéfinir les segments de l’image exécutable au moment du chargement en utilisant des adresses aléatoires tirées d’un espace d’adressage virtuel de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, l’éditeur de liens active **/HIGHENTROPYVA** pour les images exécutables 64 bits. Cette option nécessite [/LARGEADDRESSAWARE](largeaddressaware.md), qui est également activé par défaut pour les images de 64 bits. **/ HIGHENTROPYVA** n’est pas applicable aux images exécutables 32 bits, où l’option est ignorée. Pour désactiver explicitement cette option, utilisez **/highentropyva : no**. Pour cette option pour avoir un effet, le [/DYNAMICBASE](dynamicbase.md) option doit également être définie.

## <a name="see-also"></a>Voir aussi

- [Options EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Défenses de sécurité d’éditeurs de logiciels Windows](https://msdn.microsoft.com/library/bb430720.aspx)
