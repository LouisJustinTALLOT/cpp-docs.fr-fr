---
title: Informations de référence sur le schéma Tasks.vs.json (C++)
ms.date: 02/11/2019
helpviewer_keywords:
- Open Folder Projects in Visual C++
ms.assetid: abd1985e-3717-4338-9e80-869db5435175
ms.openlocfilehash: d0f62f6cddf3701da391880532bd2f554cc19130
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315051"
---
# <a name="tasksvsjson-c"></a>Tasks.vs.json (C++)

Un fichier `tasks.vs.json` peut être ajouté à un projet Dossier ouvert pour définir une tâche arbitraire, puis l’appeler à partir du menu contextuel **Explorateur de solutions**. Les projets CMake n’utilisent pas ce fichier car toutes les commandes de génération sont spécifiées dans `CMakeLists.txt`. Pour les systèmes de génération autres que CMake, c’est là que vous pouvez spécifier vos commandes de génération et appeler des scripts de génération. Pour obtenir des informations générales sur l’utilisation de tasks.vs.json, consultez [Personnaliser les tâches de génération et de débogage pour le développement « Dossier ouvert »](/visualstudio/ide/customize-build-and-debug-tasks-in-visual-studio).

