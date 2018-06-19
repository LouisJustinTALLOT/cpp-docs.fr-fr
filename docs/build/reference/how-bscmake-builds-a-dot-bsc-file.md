---
title: Comment BSCMAKE génère une. Fichier bsc | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cdc8a2840e3beb1272b33b2794f70a979684f46
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373486"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Génération d'un fichier .bsc par BSCMAKE
BSCMAKE génère ou régénère un fichier .bsc de la manière la plus efficace que possible. Pour éviter d’éventuels problèmes, il est important de comprendre le processus de génération.  
  
 Lors de la génération d’un fichier d’informations BSCMAKE, elle tronque les fichiers .sbr de longueur nulle. Pendant une génération ultérieure du même fichier, un fichier .sbr de longueur nulle (ou vide) indique à BSCMAKE ne qu’aucune nouvelle contribution pour rendre le fichier .sbr. Il informe BSCMAKE qu’une mise à jour de la partie du fichier n’est pas nécessaire et une génération incrémentielle est suffisante. Lors de chaque génération (sauf si l’option /n est spécifiée), BSCMAKE essaie d’abord à jour le fichier de façon incrémentielle à l’aide uniquement les fichiers .sbr qui ont été modifiés.  
  
 BSCMAKE recherche un fichier .bsc portant le nom spécifié avec l’option/o. Si/o n’est pas spécifiée, BSCMAKE recherche un fichier qui a le nom de base du premier fichier .sbr et une extension .bsc. Si le fichier existe, BSCMAKE effectue une génération incrémentielle du fichier d’informations parcourir uniquement les fichiers .sbr qui contribuent à l’aide de. Si le fichier n’existe pas, BSCMAKE effectue une génération complète à l’aide de tous les fichiers .sbr. Les règles pour les builds sont les suivantes :  
  
-   Pour une génération complète réussisse, tous les spécifié les fichiers .sbr doivent exister et ne doivent pas être tronqués. Si un fichier .sbr est tronqué, vous devez le reconstruire (par recompilation ou assemblage) avant d’exécuter BSCMAKE.  
  
-   Pour une génération incrémentielle réussisse, le fichier .bsc doit exister. Tous les fichiers .sbr contributeurs, même vides, il doit exister et doit être spécifié sur la ligne de commande BSCMAKE. Si vous omettez un fichier .sbr à partir de la ligne de commande, BSCMAKE élimine sa contribution à partir du fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’un fichier .bsc](../../build/reference/building-a-dot-bsc-file.md)