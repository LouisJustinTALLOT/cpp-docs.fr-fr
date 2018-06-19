---
title: Tools.ini et NMAKE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 860a334274a3a1a4ac9e11c3e7b5e9a0f136ecc0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380548"
---
# <a name="toolsini-and-nmake"></a>Tools.ini et NMAKE
NMAKE lit Tools.ini avant de lire les makefiles, sauf si /R est utilisée. Il recherche Tools.ini tout d’abord dans le répertoire actif, puis dans le répertoire spécifié par la variable d’environnement INIT. La section des paramètres NMAKE dans le fichier d’initialisation commence par `[NMAKE]` et peut contenir toutes les informations d’un makefile. Spécifiez un commentaire sur une ligne séparée commençant par un signe dièse (#).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution de NMAKE](../build/running-nmake.md)