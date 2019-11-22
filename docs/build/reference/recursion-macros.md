---
title: Macros récursives
description: Décrit les macros que vous utilisez pour appeler NMAKE dans des sessions récursives.
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303154"
---
# <a name="recursion-macros"></a>Macros récursives

Utilisez les macros récursivité pour appeler NMAKE de manière récursive. Les sessions récursives héritent des macros de la ligne de commande et de la variable d’environnement, ainsi que des informations sur Tools. ini. Ils n’héritent pas des règles d’inférence définies par Makefile ni des `.SUFFIXES` et des spécifications de `.PRECIOUS`. Il existe trois façons de passer des macros à une session NMAKE récursive : définissez une variable d’environnement avec une commande :::no-loc text="SET"::: avant l’appel récurrent. Définissez une macro dans la commande pour l’appel récurrent. Ou définissez une macro dans Tools. ini.

|Macro|Définition|
|-----------|----------------|
|**MAKE**|Commande utilisée à l’origine pour appeler NMAKE.<br /><br /> La macro `$(MAKE)` donne le chemin d’accès complet à NMAKE. exe.|
|**MAKEDIR**|Répertoire actif lors de l’appel de NMAKE.|
|**MAKEFLAGS**|Options actuellement en vigueur. À utiliser en tant que `/$(MAKEFLAGS)`. L’option **/f** n’est pas incluse.|

## <a name="see-also"></a>Voir aussi

[Macros spéciales de NMAKE](special-nmake-macros.md)
