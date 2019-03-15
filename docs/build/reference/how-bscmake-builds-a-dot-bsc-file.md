---
title: Génération d'un fichier .bsc par BSCMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- browse information files (.bsc), building
ms.assetid: 8512b33e-c856-44a2-87bd-01ab10b52a95
ms.openlocfilehash: 6f721641e021396f112bfe4c075ca0f524100d1f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821233"
---
# <a name="how-bscmake-builds-a-bsc-file"></a>Génération d'un fichier .bsc par BSCMAKE

BSCMAKE génère ou régénère un fichier .bsc dans le moyen le plus efficace que possible. Pour éviter d’éventuels problèmes, il est important de comprendre le processus de génération.

Lors de la génération d’un fichier d’informations de consultation BSCMAKE, elle tronque les fichiers .sbr de longueur nulle. Pendant une génération ultérieure du même fichier, un fichier .sbr de longueur nulle (ou vide) indique à BSCMAKE ne qu’aucune nouvelle contribution pour rendre le fichier .sbr. Il informe BSCMAKE qu’une mise à jour de cette partie du fichier n’est pas nécessaire et une build incrémentielle sera suffisante. Lors de chaque génération (sauf si l’option /n est spécifiée), BSCMAKE essaie d’abord de mettre à jour le fichier de façon incrémentielle avec uniquement les fichiers .sbr qui ont été modifiés.

BSCMAKE recherche un fichier .bsc qui porte le nom spécifié avec l’option/o. Si/o n’est pas spécifiée, BSCMAKE recherche un fichier qui a le nom de base du premier fichier .sbr et une extension .bsc. Si le fichier existe, BSCMAKE effectue une génération incrémentielle du fichier d’informations de navigation en utilisant uniquement les fichiers .sbr contribue à. Si le fichier n’existe pas, BSCMAKE effectue une génération complète à l’aide de tous les fichiers .sbr. Les règles pour les builds sont les suivantes :

- Pour une génération complète réussisse, tous spécifiés des fichiers .sbr doivent exister et ne doivent pas être tronqués. Si un fichier .sbr est tronqué, vous devez le reconstruire (par recompilation ou assemblage) avant d’exécuter BSCMAKE.

- Pour une build incrémentielle réussisse, le fichier .bsc doit exister. Tous les fichiers .sbr contributeurs, même vides, il doit exister et doit être spécifié sur la ligne de commande BSCMAKE. Si vous omettez un fichier .sbr à partir de la ligne de commande, BSCMAKE supprime sa contribution à partir du fichier.

## <a name="see-also"></a>Voir aussi

[Génération d’un fichier .bsc](building-a-dot-bsc-file.md)
