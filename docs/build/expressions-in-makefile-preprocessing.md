---
title: Expressions de prétraitement d’un Makefile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- preprocessing makefiles
- expressions [C++], makefile preprocessing
- makefiles, preprocessing
ms.assetid: 37f0f413-97e0-452c-a83f-3c9002c44c92
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04a53e5e6fe45c2c846cae3fb9e973fe1c712107
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367266"
---
# <a name="expressions-in-makefile-preprocessing"></a>Expressions utilisées dans le prétraitement d'un makefile
Le **! IF** ou **! Si** `constantexpression` se compose de constantes entières (notation décimale ou en langage C), les constantes de chaîne ou de commandes. Utilisez des parenthèses pour regrouper les expressions. Les expressions utiliser C-style entier long signé arithmétiques ; nombres se présentent sous forme de 32 bits de complément à 2 comprise entre - 2147483648 et 2147483647.  
  
 Expressions peuvent utiliser des opérateurs qui agissent sur des valeurs constantes, les codes de sortie des commandes, chaînes, macros et chemins d’accès de système de fichiers.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Sur quels éléments souhaitez-vous obtenir des informations supplémentaires ?  
 [Opérateurs de prétraitement d’un makefile](../build/makefile-preprocessing-operators.md)  
  
 [Exécution d’un programme en prétraitement](../build/executing-a-program-in-preprocessing.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prétraitement d’un makefile](../build/makefile-preprocessing.md)