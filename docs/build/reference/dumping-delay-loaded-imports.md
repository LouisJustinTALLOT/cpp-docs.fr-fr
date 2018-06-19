---
title: Dump des importations à chargement différé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13f832f0ea7aaf7b766141ce7df4f83f21e1cdca
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372865"
---
# <a name="dumping-delay-loaded-imports"></a>Dump des importations à chargement différé
Importations à chargement différé peuvent être extraites à l’aide de [dumpbin /imports](../../build/reference/imports-dumpbin.md) et présentent des informations légèrement différentes importations standard. Ils sont isolés dans leur propre section de vidage /imports et sont étiquetés explicitement en tant qu’importations à chargement différé. S’il existe de décharger les informations présentes dans l’image, qui est indiquée. Si des informations de liaison présents, le cachet de date/heure de la DLL cible est indiqué, ainsi que les adresses liées des importations.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)