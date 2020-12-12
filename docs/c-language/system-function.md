---
description: 'En savoir plus sur : fonction système'
title: system (fonction)
ms.date: 11/04/2016
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
ms.openlocfilehash: 094fb3be58c1ff82c823ff79c4181a46b7ddf14c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114378"
---
# <a name="system-function"></a>system (fonction)

**ANSI 4.10.4.5** Contenu et mode d'exécution de la chaîne par la fonction **system**

La fonction **system** exécute une commande interne du système d'exploitation ou un fichier .EXE, .COM (.CMD sur Windows NT) ou .BAT à partir d'un programme C plutôt que de la ligne de commande.

La fonction system recherche l'interpréteur de commandes (généralement CMD.EXE dans le système d'exploitation Windows NT ou COMMAND.COM dans Windows). La fonction system passe ensuite la chaîne d’arguments à l’interpréteur de commandes.

Pour plus d'informations, voir [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).

## <a name="see-also"></a>Voir aussi

[Fonctions de la bibliothèque](../c-language/library-functions.md)
