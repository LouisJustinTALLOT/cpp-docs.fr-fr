---
title: Génération d’une bibliothèque d’importation et d’un fichier d’exportation | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c832ee24d500eba28c14713d1c0a092baf90a440
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894614"
---
# <a name="building-an-import-library-and-export-file"></a>Génération d'une bibliothèque d'importation et d'un fichier d'exportation

Pour générer une bibliothèque d’importation et exportation de fichier, utilisez la syntaxe suivante :

> **LIB /DEF**[**:**<em>deffile</em>] [*options*] [*objfiles*] [*bibliothèques*]

Lorsque l’option /DEF est spécifiée, LIB crée les fichiers de sortie à partir de spécifications d’exportation qui sont passées dans la commande LIB. Il existe trois méthodes pour spécifier des exportations, répertoriées dans l’ordre d’utilisation recommandé :

1. Un **__declspec (dllexport)** définition de la *objfiles* ou *bibliothèques*

2. Une spécification de /EXPORT :*nom* sur la ligne de commande LIB

3. Une définition dans un **exportations** instruction dans un *deffile*

Ce sont les mêmes méthodes que vous utilisez pour spécifier des exportations lors de la liaison d’un programme exportateur. Un programme peut utiliser plusieurs méthodes. Vous pouvez spécifier les parties de la commande LIB (par exemple plusieurs *objfiles* ou des spécifications /EXPORT) dans un fichier de commandes dans la commande LIB, tout comme vous pouvez dans une commande de lien.

Les options suivantes s’appliquent à la création d’une bibliothèque d’importation et exportation de fichier :

> **/ OUT :** *importer*  

Substitue le nom de fichier de sortie par défaut pour le *importer* bibliothèque en cours de création. Lorsque /OUT n’est pas spécifié, le nom par défaut est le nom de base de la bibliothèque dans la commande LIB et l’extension ou le premier fichier objet. lib. Le fichier d’exportation porte le même nom que la bibliothèque d’importation et l’extension. exp.

> **/ EXPORT :** *nom d’entrée* \[ **=** *internalname*]\[,**\@** <em>ordinale</em>\[, **NONAME**]]\[, **données**]

Exporte une fonction à partir de votre programme afin d’appeler la fonction d’autres programmes. Vous pouvez également exporter des données (à l’aide de la **données** mot clé). Exportations sont généralement définies dans une DLL.

Le *nom d’entrée* est le nom de la fonction ou élément de données tel qu’il doit être utilisé par le programme appelant. Si vous le souhaitez, vous pouvez spécifier le *internalname* en tant que fonction connue dans le programme de définition ; par défaut, *internalname* est identique à *nom d’entrée*. Le *ordinale* spécifie un index dans la table d’exportation dans la plage comprise entre 1 et 65 535, si vous ne spécifiez pas *ordinale*, LIB en assigne un. Le **NONAME** mot clé exporte la fonction uniquement comme ordinal, sans un *nom d’entrée*. Le **données** mot clé est utilisé pour exporter des objets de données uniquement.

> **/ INCLUDE :** *symbole*

Ajoute l’objet *symbole* à la table de symboles. Cette option est utile pour forcer l’utilisation d’un objet de bibliothèque qui sinon ne serait pas inclus.

Notez que si vous créez votre bibliothèque d’importation dans une étape préliminaire, avant de créer votre fichier .dll, vous devez passer le même ensemble de fichiers objets lors de la génération du fichier .dll que vous avez passé lors de la création de la bibliothèque d’importation.

## <a name="see-also"></a>Voir aussi

[Utilisation de bibliothèques d’importation et de fichiers d’exportation](../../build/reference/working-with-import-libraries-and-export-files.md)