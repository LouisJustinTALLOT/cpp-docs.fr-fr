---
title: Macros récursives
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: c04b23d4c8116fdf898c2f732b63c5e02adf5661
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416408"
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
