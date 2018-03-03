---
title: "Exécution d’un programme en prétraitement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef000f6611c9cb3794da8e46e6b905e57d5ecf92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="executing-a-program-in-preprocessing"></a>Exécution d'un programme en prétraitement
Pour utiliser le code de sortie d’une commande lors du prétraitement, spécifiez la commande, avec tous les arguments, entre crochets ([]). Les macros sont développées avant l’exécution de la commande. NMAKE remplace la spécification de la commande avec le code de sortie de la commande, qui peut être utilisé dans une expression pour contrôler le prétraitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions utilisées dans le prétraitement d’un makefile](../build/expressions-in-makefile-preprocessing.md)