---
title: Tools.ini et NMAKE | Microsoft Docs
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
ms.openlocfilehash: 84406886c9aa0c0053ed7c183912bf8a7f1f4771
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723578"
---
# <a name="toolsini-and-nmake"></a>Tools.ini et NMAKE

NMAKE lit Tools.ini avant de lire les makefiles, sauf si /R est utilisée. Il recherche Tools.ini tout d’abord dans le répertoire actif, puis dans le répertoire spécifié par la variable d’environnement INIT. La section des paramètres NMAKE dans le fichier d’initialisation commence par `[NMAKE]` et peut contenir toutes les informations makefile. Spécifiez un commentaire sur une ligne séparée commençant par un signe dièse (#).

## <a name="see-also"></a>Voir aussi

[Exécution de NMAKE](../build/running-nmake.md)