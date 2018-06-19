---
title: Où définir des Macros | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf3e87a50362c770d45f00c4dc17ac3d264f611
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380912"
---
# <a name="where-to-define-macros"></a>Où définir des macros
Définissez les macros dans une ligne de commande, fichier de commandes, un makefile ou le fichier Tools.ini.  
  
 Dans un makefile ou le fichier Tools.ini, chaque définition de macro doit apparaître sur une ligne distincte et ne peut pas commencer par un espace ou une tabulation. Des espaces ou des onglets autour du signe égal sont ignorés. Tous les [chaîne de caractères](../build/defining-an-nmake-macro.md) sont des littéraux, des espaces et les guillemets de délimitation compris.  
  
 Dans une ligne de commande ou un fichier de commandes, les espaces et tabulations délimitent les arguments et ne peuvent pas entourer le signe égal. Si `string` incorpore des espaces ou des tabulations, mettez la chaîne ou l’intégralité de la macro entre guillemets doubles (« »).  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’une macro NMAKE](../build/defining-an-nmake-macro.md)