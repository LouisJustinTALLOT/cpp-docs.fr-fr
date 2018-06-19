---
title: Macros récursives | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759deaff6014cbba40c97f9d627baf6a800732f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368959"
---
# <a name="recursion-macros"></a>Macros récursives
Utiliser des macros de récursivité pour appeler NMAKE de manière récursive. Les sessions récursives héritent des macros de ligne de commande et la variable d’environnement et des informations concernant Tools.ini. Ils n’héritent pas des règles d’inférence définies makefile ou **. SUFFIXES** et **. PRÉCIEUX** spécifications. Pour passer des macros à une session NMAKE récursive, définir une variable d’environnement avec jeu avant l’appel récursif, définissez une macro dans la commande pour l’appel récursif ou définissez une macro dans Tools.ini.  
  
|Macro|Définition|  
|-----------|----------------|  
|**RENDRE**|Commande utilisée initialement pour appeler NMAKE.<br /><br /> La macro $ (Make) donne le chemin d’accès complet à nmake.exe.|  
|**MAKEDIR**|Répertoire actif où NMAKE a été appelé.|  
|**MAKEFLAGS**|Options actuellement en vigueur. Utiliser comme `/$(MAKEFLAGS)`.  Notez que /F n’est pas inclus.|  
  
## <a name="see-also"></a>Voir aussi  
 [Macros spéciales de NMAKE](../build/special-nmake-macros.md)