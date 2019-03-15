---
title: Exécution de NMAKE
ms.date: 09/05/2018
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: dac5e9c1676278d150dd9802697a8ae8959a40e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825810"
---
# <a name="running-nmake"></a>Exécution de NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*option* ...] [*macros* ...] [*cibles* ...] [**\@**<em>/commandfile</em> ...]

## <a name="remarks"></a>Notes

Builds NMAKE uniquement spécifiés *cibles* ou, si aucun n’est spécifié, la première cible dans le makefile. La première cible du makefile peut être un [pseudocible](pseudotargets.md) qui génère d’autres cibles. NMAKE utilise les makefiles définis avec /F ; Si /F n’est pas spécifié, il utilise le fichier Makefile dans le répertoire actif. Si aucun makefile n’est spécifié, il utilise des règles d’inférence pour générer de ligne de commande *cibles*.

Le */commandfile* fichier texte (ou fichier réponse) contient l’entrée de ligne de commande. Autres entrées peuvent précéder ou suivre \@ */commandfile*. Un chemin d’accès est autorisé. Dans */commandfile*, sauts de ligne sont considérés comme des espaces. Placez les définitions de macros entre guillemets s’ils contiennent des espaces.

## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?

[Options de NMAKE](nmake-options.md)

[Tools.ini et NMake](tools-ini-and-nmake.md)

[Codes de sortie de NMAKE](exit-codes-from-nmake.md)

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](nmake-reference.md)
