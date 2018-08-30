---
title: -HIGHENTROPYVA | Microsoft Docs
ms.custom: ''
ms.date: 06/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /HIGHENTROPYVA
dev_langs:
- C++
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5fec9314be9d69e2cb0af2a98884bd78de1ff679
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202069"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

Spécifie si l’image exécutable prend en charge la randomisation du format d’espace d’adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **/ HIGHENTROPYVA**[**: NO**]

## <a name="remarks"></a>Notes

Cette option modifie l’en-tête d’un *image exécutable*, un fichier .dll ou .exe, pour indiquer si ASLR avec des adresses 64 bits est pris en charge. Quand cette option est définie au niveau d’un fichier exécutable et de tous les modules dont il dépend, un système d’exploitation qui prend en charge l’ASLR 64 bits peut rebaser les segments de l’image exécutable au moment du chargement en utilisant des adresses aléatoires tirées d’un espace d’adressage virtuel de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, l’éditeur de liens active **/HIGHENTROPYVA** pour les images exécutables 64 bits. Cette option nécessite [/LARGEADDRESSAWARE](largeaddressaware.md), qui est également activé par défaut pour les images de 64 bits. **/ HIGHENTROPYVA** n’est pas applicable aux images exécutables 32 bits, où l’option est ignorée. Pour désactiver explicitement cette option, utilisez **/highentropyva : no**. Pour cette option pour avoir un effet, le [/DYNAMICBASE](dynamicbase.md) option doit également être définie.

## <a name="see-also"></a>Voir aussi

- [Options EDITBIN](editbin-options.md)
- [/DYNAMICBASE](dynamicbase.md)
- [Défenses de sécurité d’éditeurs de logiciels Windows](https://msdn.microsoft.com/library/bb430720.aspx)
