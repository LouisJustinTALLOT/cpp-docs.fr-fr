---
title: Exécution de NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdc9d89dbc0e77a8002cc34e5d010ee49d761da4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706691"
---
# <a name="running-nmake"></a>Exécution de NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*option* ...] [*macros* ...] [*cibles* ...] [**\@**<em>/commandfile</em> ...]

## <a name="remarks"></a>Notes

Builds NMAKE uniquement spécifiés *cibles* ou, si aucun n’est spécifié, la première cible dans le makefile. La première cible du makefile peut être un [pseudocible](../build/pseudotargets.md) qui génère d’autres cibles. NMAKE utilise les makefiles définis avec /F ; Si /F n’est pas spécifié, il utilise le fichier Makefile dans le répertoire actif. Si aucun makefile n’est spécifié, il utilise des règles d’inférence pour générer de ligne de commande *cibles*.

Le */commandfile* fichier texte (ou fichier réponse) contient l’entrée de ligne de commande. Autres entrées peuvent précéder ou suivre \@ */commandfile*. Un chemin d’accès est autorisé. Dans */commandfile*, sauts de ligne sont considérés comme des espaces. Placez les définitions de macros entre guillemets s’ils contiennent des espaces.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Options de NMAKE](../build/nmake-options.md)

[Tools.ini et NMake](../build/tools-ini-and-nmake.md)

[Codes de sortie de NMAKE](../build/exit-codes-from-nmake.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](../build/nmake-reference.md)