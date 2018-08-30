---
title: Génération de manifeste à la ligne de commande | Microsoft Docs
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
ms.openlocfilehash: 97e2bb423deb4a50da0cf0772ae81e19bb4b48eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220725"
---
# <a name="manifest-generation-at-the-command-line"></a>Génération de manifeste au niveau de la ligne de commande
Lorsque vous générez des applications C/C++ à partir de la ligne de commande à l’aide de nmake ou des outils similaires, le manifeste est généré une fois que l’éditeur de liens a traité tous les fichiers objets et construit le fichier binaire final. L’éditeur de liens recueille des informations d’assembly stockées dans les fichiers objets et combine ces informations dans un fichier de manifeste final. Par défaut, l’éditeur de liens génère un fichier nommé < nom_fichier_binaire >. \<extension > .manifest pour décrire le fichier binaire final. L’éditeur de liens n’incorpore pas un fichier manifeste dans le fichier binaire et ne peut générer un manifeste comme un fichier externe. Il existe plusieurs façons d’incorporer un manifeste dans le fichier binaire final, par exemple à l’aide de la [outil manifeste (mt.exe)](https://msdn.microsoft.com/library/aa375649) ou en compilant le manifeste en un fichier de ressources. Il est important de n’oubliez pas que des règles spécifiques doivent être suivies lors de l’incorporation d’un manifeste dans le fichier binaire final pour activer des fonctionnalités telles que la liaison incrémentielle, signature, et Modifier & Continuer. Ces d’autres options sont traitées dans [Comment : incorporer un manifeste à l’intérieur d’une Application C/C++](../build/how-to-embed-a-manifest-inside-a-c-cpp-application.md) lors de la création de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Manifestes](https://msdn.microsoft.com/library/aa375365)   
 [/INCREMENTAL (lier par incrément)](../build/reference/incremental-link-incrementally.md)   
 [Assemblys de nom fort (signature d’Assembly) (C++ / c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)   
 [Modifier & Continuer](/visualstudio/debugger/edit-and-continue)   
 [Présentation de la génération de manifeste pour les programmes C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)