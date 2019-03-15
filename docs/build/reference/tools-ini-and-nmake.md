---
title: Tools.ini et NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, reading files
- Tools.ini and NMake
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
ms.openlocfilehash: 38eebb3aaf07438da85b0cfe6bd3f26fb5d6db29
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825524"
---
# <a name="toolsini-and-nmake"></a>Tools.ini et NMAKE

NMAKE lit Tools.ini avant de lire les makefiles, sauf si /R est utilisée. Il recherche Tools.ini tout d’abord dans le répertoire actif, puis dans le répertoire spécifié par la variable d’environnement INIT. La section des paramètres NMAKE dans le fichier d’initialisation commence par `[NMAKE]` et peut contenir toutes les informations makefile. Spécifiez un commentaire sur une ligne séparée commençant par un signe dièse (#).

## <a name="see-also"></a>Voir aussi

[Exécution de NMAKE](running-nmake.md)