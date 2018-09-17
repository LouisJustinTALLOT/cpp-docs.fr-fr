---
title: Macros récursives | Microsoft Docs
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
ms.openlocfilehash: f91a5f327686a522608b6eec9fd7106cbab00028
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702038"
---
# <a name="recursion-macros"></a>Macros récursives

Utiliser des macros récursives pour appeler NMAKE de manière récursive. Les sessions récursives héritent des macros de ligne de commande et la variable d’environnement et les informations de Tools.ini. Ils n’héritent pas des règles d’inférence définies makefile ou **. SUFFIXES** et **. PRÉCIEUX** spécifications. Pour passer des macros à une session NMAKE récursive, définissez une variable d’environnement avec SET avant l’appel récursif, définir une macro dans la commande pour l’appel récursif ou définir une macro Tools.ini.

|Macro|Définition|
|-----------|----------------|
|**RENDRE**|Commande utilisée initialement pour appeler NMAKE.<br /><br /> La macro $ (Make) donne le chemin d’accès complet à nmake.exe.|
|**MAKEDIR**|Répertoire actif où NMAKE a été appelé.|
|**MAKEFLAGS**|Options actuellement en vigueur. Utiliser comme `/$(MAKEFLAGS)`.  Notez que /F n’est pas inclus.|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](../build/special-nmake-macros.md)