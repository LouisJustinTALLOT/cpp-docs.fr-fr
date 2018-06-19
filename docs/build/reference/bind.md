---
title: -BIND | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bind
dev_langs:
- C++
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b77c778017dc78235948e8d23db136c1f63ab12d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372429"
---
# <a name="bind"></a>/BIND
```  
/BIND[:PATH=path]  
```  
  
## <a name="remarks"></a>Notes  
 Cette option définit les adresses des points d’entrée dans la table d’adresses importer un fichier exécutable ou DLL. Utilisez cette option pour réduire le temps de chargement d’un programme.  
  
 Spécifiez le fichier exécutable du programme et les DLL dans le *fichiers* argument sur la ligne de commande EDITBIN. Le paramètre facultatif *chemin d’accès* argument de /BIND spécifie l’emplacement des DLL utilisées par les fichiers spécifiés. Séparez les répertoires multiples par un point-virgule (**;**). Si *chemin d’accès* n’est pas spécifié, EDITBIN parcourt les répertoires spécifiés dans la variable d’environnement PATH. Si *chemin d’accès* est spécifié, EDITBIN ignore la variable de chemin d’accès.  
  
 Par défaut, le chargeur de programme définit les adresses des points d’entrée lors du chargement d’un programme. La durée de ce processus varie selon le nombre de DLL et le nombre de points d’entrée référencé dans le programme. Si un programme a été modifié avec /BIND et si les adresses de base pour le fichier exécutable et ses DLL éviter les conflits avec les DLL qui sont déjà chargées, le système d’exploitation n’a pas besoin de définir ces adresses. Dans une situation où les fichiers sont correctement en fonction, le système d’exploitation déplace les DLL du programme et recalcule les adresses de point d’entrée, qui ajoute au moment du chargement du programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)