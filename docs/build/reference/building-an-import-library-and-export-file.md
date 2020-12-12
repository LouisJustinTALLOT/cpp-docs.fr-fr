---
description: 'En savoir plus sur : génération d’une bibliothèque d’importation et d’un fichier d’exportation'
title: Génération d'une bibliothèque d'importation et d'un fichier d'exportation
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
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
ms.openlocfilehash: 8fbd06ce06d77721e64294b88632933b3ad71a03
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179510"
---
# <a name="building-an-import-library-and-export-file"></a>Génération d'une bibliothèque d'importation et d'un fichier d'exportation

Pour générer une bibliothèque d’importation et un fichier d’exportation, utilisez la syntaxe suivante :

> **Lib/def**[**:**<em>deffile</em>] [*options*] [*objfiles*] [*bibliothèques*]

Lorsque l’option/DEF est spécifiée, LIB crée les fichiers de sortie à partir des spécifications d’exportation qui sont transmises dans la commande LIB. Il existe trois méthodes pour spécifier des exportations, répertoriées dans l’ordre d’utilisation recommandé :

1. Une **`__declspec(dllexport)`** définition dans l’un des *objfiles* ou *bibliothèques*

1. Une spécification de/EXPORT :*Name* sur la ligne de commande lib

1. Définition dans une instruction **exports** dans un *deffile*

Il s’agit des mêmes méthodes que celles utilisées pour spécifier des exportations lors de la liaison d’un programme d’exportation. Un programme peut utiliser plusieurs méthodes. Vous pouvez spécifier des parties de la commande LIB (par exemple, plusieurs spécifications *objfiles* ou/Export) dans un fichier de commandes dans la commande lib, comme vous le feriez dans une commande Link.

Les options suivantes s’appliquent à la création d’une bibliothèque d’importation et d’un fichier d’exportation :

> **/Out :** *Importer*

Remplace le nom de fichier de sortie par défaut pour la bibliothèque d' *importation* en cours de création. Lorsque/OUT n’est pas spécifié, le nom par défaut est le nom de base du premier fichier objet ou bibliothèque dans la commande LIB et l’extension. lib. Le fichier d’exportation reçoit le même nom de base que la bibliothèque d’importation et l’extension. exp.

> **/Export :** *entryname* \[ **=** *InternalName*] \[ , **\@** <em>ordinal</em> \[ , **NoName**]] \[ , **données**]

Exporte une fonction à partir de votre programme pour permettre à d’autres programmes d’appeler la fonction. Vous pouvez également exporter des données (à l’aide du mot clé **Data** ). Les exportations sont généralement définies dans une DLL.

L’argument *entryname* est le nom de la fonction ou de l’élément de données tel qu’il doit être utilisé par le programme appelant. Si vous le souhaitez, vous pouvez spécifier le *InternalName* comme fonction connue dans le programme de définition. par défaut, *InternalName* est identique à *entryname*. L' *ordinal* spécifie un index dans la table d’exportation de la plage comprise entre 1 et 65 535 ; Si vous ne spécifiez pas d' *ordinal*, lib en assigne un. Le mot clé **NoName** exporte la fonction uniquement en tant qu’ordinal, sans *entryname*. Le mot clé **Data** est utilisé pour exporter uniquement les objets de données.

> **/Include :** *symbole*

Ajoute le *symbole* spécifié à la table de symboles. Cette option est utile pour forcer l’utilisation d’un objet de bibliothèque qui, sinon, ne serait pas inclus.

Notez que si vous créez votre bibliothèque d’importation à une étape préliminaire, avant de créer votre fichier. dll, vous devez passer le même ensemble de fichiers objets lors de la génération du fichier. dll, comme vous l’avez passé lors de la génération de la bibliothèque d’importation.

## <a name="see-also"></a>Voir aussi

[Utilisation de bibliothèques d’importation et de fichiers d’exportation](working-with-import-libraries-and-export-files.md)
