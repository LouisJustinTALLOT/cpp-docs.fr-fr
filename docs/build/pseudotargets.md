---
title: Pseudocibles
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
ms.openlocfilehash: 34b2b2f0d54a6e11bdfd6e818eb08d01721d80e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414835"
---
# <a name="pseudotargets"></a>Pseudocibles

Une pseudocible est une étiquette utilisée à la place d’un nom de fichier dans une ligne de dépendance. Il est interprété comme un fichier qui n’existe pas et par conséquent, est obsolète. NMAKE suppose le que horodatage d’une pseudocible est la plus récente de tous ses éléments dépendants. Si elle n’a aucune dépendance, l’heure actuelle est supposé. Si une pseudocible est utilisée en tant que cible, ses commandes sont toujours exécutées. Une pseudocible utilisée comme dépendant doit également apparaître en tant que cible dans une autre dépendance. Toutefois, cette dépendance n’a pas besoin d’avoir un bloc de commandes.

Noms des pseudocibles obéissent les règles de syntaxe de nom de fichier pour les cibles. Toutefois, si le nom n’a pas d’extension (autrement dit, s’il ne contient pas une période), il peut dépasser la limite de 8 caractères pour les noms de fichiers et peut comporter jusqu'à 256 caractères.

## <a name="see-also"></a>Voir aussi

[Cibles](../build/targets.md)
