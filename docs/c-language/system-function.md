---
title: Fonction system | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51c9e9e348f1cd1fbae9612c2d2ad1988af3b009
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386733"
---
# <a name="system-function"></a>system (fonction)
**ANSI 4.10.4.5** Contenu et mode d'exécution de la chaîne par la fonction **system**  
  
 La fonction **system** exécute une commande interne du système d'exploitation ou un fichier .EXE, .COM (.CMD sur Windows NT) ou .BAT à partir d'un programme C plutôt que de la ligne de commande.  
  
 La fonction system recherche l'interpréteur de commandes (généralement CMD.EXE dans le système d'exploitation Windows NT ou COMMAND.COM dans Windows). La fonction system passe ensuite la chaîne d’arguments à l’interpréteur de commandes.  
  
 Pour plus d'informations, voir [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions des bibliothèques](../c-language/library-functions.md)