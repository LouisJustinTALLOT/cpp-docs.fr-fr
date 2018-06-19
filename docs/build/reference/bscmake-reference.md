---
title: Référence BSCMAKE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de8e71a448c71fd18ba9cba99cb9b7347598489c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370616"
---
# <a name="bscmake-reference"></a>Référence BSCMAKE
> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.  
  
 Microsoft Browse Information Maintenance Utility (BSCMAKE.EXE) génère un fichier d'informations de consultation (.bsc) à partir des fichiers .sbr créés lors de la compilation. Certains des outils tiers utilisent des fichiers .bsc pour l’analyse du code. 
  
 Quand vous générez votre programme, vous pouvez créer automatiquement un fichier d'informations de consultation pour votre programme en utilisant BSCMAKE pour générer le fichier. Vous n'avez pas besoin de savoir comment exécuter BSCMAKE si vous créez votre fichier d'informations de consultation dans l'environnement de développement Visual C++. Toutefois, vous pouvez lire cette rubrique pour comprendre les choix disponibles.  
  
 Si vous générez votre programme en dehors de l'environnement de développement, vous pouvez encore créer un fichier .bsc personnalisé que vous pouvez examiner dans l'environnement. Exécutez BSCMAKE sur les fichiers .sbr que vous avez créés lors de la compilation.  
  
> [!NOTE]
>  Vous pouvez démarrer cet outil uniquement à partir de l’invite de commandes Visual Studio Developer. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.  
  
 Cette section comprend les rubriques suivantes :  
  
-   [Génération de fichiers d’informations de consultation : vue d’ensemble](../../build/reference/building-browse-information-files-overview.md)  
  
-   [Génération d’un fichier .bsc](../../build/reference/building-a-dot-bsc-file.md)  
  
-   [Ligne de commande BSCMAKE](../../build/reference/bscmake-command-line.md)  
  
-   [Fichier de commande BSCMAKE](../../build/reference/bscmake-command-file-response-file.md)  
  
-   [Options BSCMAKE](../../build/reference/bscmake-options.md)  
  
-   [Codes de sortie BSCMAKE](../../build/reference/bscmake-exit-codes.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)