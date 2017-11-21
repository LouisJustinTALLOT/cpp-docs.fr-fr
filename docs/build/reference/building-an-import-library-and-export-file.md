---
title: "Création d’une bibliothèque d’importation et d’un fichier d’exportation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs: C++
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 05368937505ff77674bb6b176ceb0e14f55384e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="building-an-import-library-and-export-file"></a>Génération d'une bibliothèque d'importation et d'un fichier d'exportation
Pour générer une bibliothèque d’importation et exportation de fichier, utilisez la syntaxe suivante :  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 Lorsque l’option /DEF est spécifiée, LIB crée les fichiers de sortie à partir de spécifications d’exportation qui sont passées dans la commande LIB. Il existe trois méthodes de spécification des exportations, répertoriées dans l’ordre d’utilisation recommandé :  
  
1.  A **__declspec (dllexport)** définition de la *objfiles* ou *bibliothèques*  
  
2.  Une spécification de /EXPORT :*nom* sur la ligne de commande LIB  
  
3.  Une définition dans un **exportations** instruction dans un`deffile`  
  
 Ce sont les mêmes méthodes que vous utilisez pour spécifier des exportations lors de la liaison d’un programme d’exportation. Un programme peut utiliser plusieurs méthodes. Vous pouvez spécifier les parties de la commande LIB (par exemple plusieurs *objfiles* ou des spécifications /EXPORT) dans un fichier de commandes dans la commande LIB, tout comme vous pouvez dans une commande LINK.  
  
 Les options suivantes s’appliquent à la création d’une bibliothèque d’importation et exportation de fichier :  
  
 / OUT : *importer*  
 Substitue le nom de fichier de sortie par défaut pour le *importer* bibliothèque en cours de création. Lors de l’option /OUT n’est pas spécifié, le nom par défaut est le nom de base de la bibliothèque dans la commande LIB et l’extension ou le premier fichier objet. lib. Le fichier d’exportation porte le même nom que la bibliothèque d’importation et de l’extension. exp.  
  
 / EXPORT : *nom d’entrée*[= *internalname*] [, @ `ordinal`[, **NONAME**]] [, **données**]  
 Exporte une fonction à partir de votre programme afin d’autoriser d’autres programmes d’appeler la fonction. Vous pouvez également exporter des données (à l’aide de la **données** mot clé). Les exportations sont généralement définies dans une DLL.  
  
 Le *nom d’entrée* est le nom de l’élément de données ou de la fonction tel qu’il doit être utilisé par le programme appelant. Si vous le souhaitez, vous pouvez spécifier le *internalname* en tant que fonction connue dans le programme de définition ; par défaut, *internalname* est identique à *nom d’entrée*. Le `ordinal` spécifie un index dans la table d’exportation compris entre 1 et 65 535 ; si vous ne spécifiez pas `ordinal`, LIB en assigne un. Le **NONAME** mot clé exporte la fonction uniquement comme ordinal, sans une *nom d’entrée*. Le **données** est utilisé pour exporter des objets de données uniquement.  
  
 / SONT LES SUIVANTES :`symbol`  
 Ajoute le symbole spécifié à la table de symboles. Cette option est utile pour forcer l’utilisation d’un objet de bibliothèque qui autrement n’est pas inclus.  
  
 Notez que si vous créez votre bibliothèque d’importation dans une étape préliminaire, avant de créer votre fichier .dll, vous devez passer le même jeu de fichiers objets lors de la génération du fichier .dll que vous avez passé lors de la création de la bibliothèque d’importation.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de bibliothèques d’importation et de fichiers d’exportation](../../build/reference/working-with-import-libraries-and-export-files.md)