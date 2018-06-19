---
title: PRJ0041 d’avertissement de génération de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0041
dev_langs:
- C++
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e845967b0a7116d6edade98b571de5bc1bcd9a1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318059"
---
# <a name="project-build-warning-prj0041"></a>Avertissement de génération de projet PRJ0041
Impossible de trouver manquant dépendance 'dépendance' fichier 'fichier'. Votre projet peut être généré, mais peut sembler obsolète tant que ce fichier se trouve.  
  
 Un fichier (fichier de ressources ou.idl/.odl, par exemple, contenait une instruction include que le système de projet n’a pas pu résoudre.  
  
 Étant donné que le système de projet ne traite pas les instructions de préprocesseur (#if, par exemple), l’instruction en fait peut-être pas partie de la build.  
  
 Pour résoudre cet avertissement, supprimez tout le code dans les fichiers .rc inutile ou ajouter des fichiers d’espace réservé du nom approprié.