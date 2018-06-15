---
title: Génération de projets externes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- external projects
- Visual C++ projects, external projects
- builds [C++], external projects
- projects [C++], external projects
- Makefile projects, external projects
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97b6aa1e5939afe55644df6529bf75ba043f20bb
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330344"
---
# <a name="building-external-projects"></a>Génération de projets externes
Un projet externe est un projet Visual C++ qui utilise un makefile ou d’autres fonctionnalités qui se situent en dehors de l’environnement de développement Visual C++ (qui sont étrangères ou extérieures à celui-ci).  
  
 Si vous disposez d’un projet externe (un projet Makefile, par exemple) que vous voulez générer dans l’environnement de développement Visual C++, créez un projet Makefile et spécifiez la sortie et la commande de génération de votre projet dans l’Assistant Application Makefile. Pour plus d’informations, consultez [Création d’un projet Makefile](../ide/creating-a-makefile-project.md).  
  
 Notez que Visual C++ n’offre plus la possibilité d’exporter un makefile pour le projet actif à partir de l’environnement de développement. Utilisez [Commutateurs de la ligne de commande Devenv](/visualstudio/ide/reference/devenv-command-line-switches) pour générer des projets Visual Studio à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de projets C++ dans Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)