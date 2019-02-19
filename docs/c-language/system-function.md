---
title: system (fonction)
ms.date: 11/04/2016
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
ms.openlocfilehash: e37de4e084de6727cf2858117945fd162f6b0d63
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151219"
---
# <a name="system-function"></a>system (fonction)

**ANSI 4.10.4.5** Contenu et mode d'exécution de la chaîne par la fonction **system**

La fonction **system** exécute une commande interne du système d'exploitation ou un fichier .EXE, .COM (.CMD sur Windows NT) ou .BAT à partir d'un programme C plutôt que de la ligne de commande.

La fonction system recherche l'interpréteur de commandes (généralement CMD.EXE dans le système d'exploitation Windows NT ou COMMAND.COM dans Windows). La fonction system passe ensuite la chaîne d’arguments à l’interpréteur de commandes.

Pour plus d'informations, voir [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)
