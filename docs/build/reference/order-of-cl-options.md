---
title: Ordre des Options CL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 165e20eefecd20ad9dec9e01b38c5eaa7926e4eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372807"
---
# <a name="order-of-cl-options"></a>Ordre des options CL
Options peuvent apparaître n’importe où sur la ligne de commande CL, à l’exception de l’option /link, qui doit avoir lieu en dernier. Le compilateur commence par les options spécifiées dans le [variable d’environnement CL](../../build/reference/cl-environment-variables.md) , puis lit la ligne de commande de gauche à droite, le traitement des fichiers de commandes dans l’ordre où il les trouve. Chaque option s’applique à tous les fichiers sur la ligne de commande. Si CL rencontre des options en conflit, elle utilise l’option la plus à droite.  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe de la ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md)