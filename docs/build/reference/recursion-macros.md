---
title: Macros récursives
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 064bc40906bcf3a126c225585a6df43443b5c38e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319237"
---
# <a name="recursion-macros"></a>Macros récursives

Utiliser des macros récursives pour appeler NMAKE de manière récursive. Les sessions récursives héritent des macros de ligne de commande et la variable d’environnement et les informations de Tools.ini. Ils n’héritent pas des règles d’inférence définies makefile ou **. SUFFIXES** et **. PRÉCIEUX** spécifications. Pour passer des macros à une session NMAKE récursive, définissez une variable d’environnement avec SET avant l’appel récursif, définir une macro dans la commande pour l’appel récursif ou définir une macro Tools.ini.

|Macro|Définition|
|-----------|----------------|
|**RENDRE**|Commande utilisée initialement pour appeler NMAKE.<br /><br /> La macro $ (Make) donne le chemin d’accès complet à nmake.exe.|
|**MAKEDIR**|Répertoire actif où NMAKE a été appelé.|
|**MAKEFLAGS**|Options actuellement en vigueur. Utiliser comme `/$(MAKEFLAGS)`.  Notez que /F n’est pas inclus.|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](special-nmake-macros.md)
