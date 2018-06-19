---
title: Exécution d’un programme en prétraitement | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da87a87a2e97736d202b7ddb9be2dbec54fed44d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367197"
---
# <a name="executing-a-program-in-preprocessing"></a>Exécution d'un programme en prétraitement
Pour utiliser le code de sortie d’une commande lors du prétraitement, spécifiez la commande, avec tous les arguments, entre crochets ([]). Les macros sont développées avant l’exécution de la commande. NMAKE remplace la spécification de la commande avec le code de sortie de la commande, qui peut être utilisé dans une expression pour contrôler le prétraitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions utilisées dans le prétraitement d’un makefile](../build/expressions-in-makefile-preprocessing.md)