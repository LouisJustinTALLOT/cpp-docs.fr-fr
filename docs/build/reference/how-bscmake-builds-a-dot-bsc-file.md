---
description: 'En savoir plus sur : Comment BSCMAKE génère un. Fichier BSC'
title: Génération d'un fichier .bsc par BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: 6d468f365f7f42be2eb393e53d72053b682ec65a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191379"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Génération d'un fichier .bsc par BSCMAKE

BSCMAKE génère ou reconstruit un fichier. bsc de la manière la plus efficace possible. Pour éviter les problèmes potentiels, il est important de comprendre le processus de génération.

Lorsque BSCMAKE génère un fichier d’informations de consultation, il tronque les fichiers. SBR à une longueur nulle. Pendant une génération suivante du même fichier, un fichier. sbr de longueur nulle (ou vide) indique à BSCMAKE que le fichier. SBR n’a pas de nouvelle contribution à effectuer. Il permet à BSCMAKE de savoir qu’une mise à jour de cette partie du fichier n’est pas requise et qu’une build incrémentielle est suffisante. Lors de chaque génération (sauf si l’option/n est spécifiée), BSCMAKE tente d’abord de mettre à jour le fichier de façon incrémentielle en utilisant uniquement les fichiers. SBR modifiés.

BSCMAKE recherche un fichier. bsc qui porte le nom spécifié avec l’option/o. Si/o n’est pas spécifié, BSCMAKE recherche un fichier qui porte le nom de base du premier fichier. SBR et une extension. bsc. Si le fichier existe, BSCMAKE effectue une génération incrémentielle du fichier d’informations de consultation en utilisant uniquement les fichiers. SBR contributeurs. Si le fichier n’existe pas, BSCMAKE effectue une génération complète à l’aide de tous les fichiers. sbr. Les règles pour les builds sont les suivantes :

- Pour qu’une génération complète aboutisse, tous les fichiers. SBR spécifiés doivent exister et ne doivent pas être tronqués. Si un fichier. SBR est tronqué, vous devez le reconstruire (en recompilant ou en assemblant) avant d’exécuter BSCMAKE.

- Pour qu’une build incrémentielle aboutisse, le fichier. bsc doit exister. Tous les fichiers. SBR contributeurs, même les fichiers vides, doivent exister et être spécifiés sur la ligne de commande BSCMAKE. Si vous omettez un fichier. SBR à partir de la ligne de commande, BSCMAKE supprime sa contribution du fichier.

## <a name="see-also"></a>Voir aussi

[Génération d’un. Fichier BSC](building-a-dot-bsc-file.md)
