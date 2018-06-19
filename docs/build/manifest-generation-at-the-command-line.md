---
title: Génération de manifeste à la ligne de commande | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f740030e48a33284a31da4ebd46f0c4d7b6ac7e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368497"
---
# <a name="manifest-generation-at-the-command-line"></a>Génération de manifeste au niveau de la ligne de commande
Lors de la génération d’applications C/C++ à partir de la ligne de commande à l’aide de nmake ou outils similaires, le manifeste est généré après que l’éditeur de liens a traité tous les fichiers objets et la génération du fichier binaire final. L’éditeur de liens recueille des informations d’assembly stockées dans les fichiers objets et les combine dans un fichier manifest final. Par défaut, l’éditeur de liens génère un fichier nommé < binary_name >. \<extension > .manifest pour décrire le fichier binaire final. L’éditeur de liens n’incorpore pas un fichier manifeste dans le fichier binaire et ne peut générer un manifeste dans un fichier externe. Il existe plusieurs façons d’incorporer un manifeste dans le fichier binaire final, par exemple à l’aide de la [outil manifeste (mt.exe)](http://msdn.microsoft.com/library/aa375649) ou en compilant le manifeste dans un fichier de ressources. Il est important de conserver à l’esprit que des règles spécifiques doivent être suivies lors de l’incorporation d’un manifeste dans le fichier binaire final pour activer des fonctionnalités telles que la liaison incrémentielle, signature, et Modifier & Continuer. Celles-ci et autres options sont décrites dans [Comment : incorporer un manifeste à l’intérieur d’une Application C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) lors de la création de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Manifestes](http://msdn.microsoft.com/library/aa375365)   
 [/INCREMENTAL (lier par incrément)](../build/reference/incremental-link-incrementally.md)   
 [Assemblys de nom fort (signature d’Assembly) (C + c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Modifier & Continuer](/visualstudio/debugger/edit-and-continue)   
 [Présentation de la génération de manifeste pour les programmes C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)