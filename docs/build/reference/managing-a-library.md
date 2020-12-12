---
description: 'En savoir plus sur : gestion d’une bibliothèque'
title: Gestion d'une bibliothèque
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: f862dfd460bb51cdf6e855c87b08b7426a5642d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199127"
---
# <a name="managing-a-library"></a>Gestion d'une bibliothèque

Le mode par défaut pour LIB consiste à créer ou à modifier une bibliothèque d’objets COFF. LIB s’exécute dans ce mode quand vous ne spécifiez pas/EXTRACT (pour copier un objet dans un fichier) ou/DEF (pour générer une bibliothèque d’importation).

Pour générer une bibliothèque à partir d’objets et/ou de bibliothèques, utilisez la syntaxe suivante :

```
LIB [options...] files...
```

Cette commande crée une bibliothèque à partir d’un ou de plusieurs *fichiers* d’entrée. Les *fichiers* peuvent être des fichiers objets COFF, des fichiers objets OMF 32 bits ou des bibliothèques COFF existantes. LIB crée une bibliothèque qui contient tous les objets dans les fichiers spécifiés. Si un fichier d’entrée est un fichier objet OMF 32 bits, LIB le convertit au format COFF avant de générer la bibliothèque. LIB ne peut pas accepter un objet OMF 32 bits qui se trouve dans une bibliothèque créée par la version 16 bits de LIB. Vous devez d’abord utiliser la bibliothèque 16 bits pour extraire l’objet. vous pouvez ensuite utiliser le fichier objet extrait comme entrée de la bibliothèque 32 bits.

Par défaut, LIB nomme le fichier de sortie à l’aide du nom de base du premier fichier d’objet ou de la bibliothèque et de l’extension. lib. Le fichier de sortie est placé dans le répertoire actif. Si un fichier existe déjà avec le même nom, le fichier de sortie remplace le fichier existant. Pour conserver une bibliothèque existante, utilisez l’option/OUT pour spécifier un nom pour le fichier de sortie.

Les options suivantes s’appliquent à la création et à la modification d’une bibliothèque :

**/LIBPATH :** *Rép*<br/>
Substitue le chemin d’accès de la bibliothèque d’environnement. Pour plus d’informations, consultez la description de [l’option de](libpath-additional-libpath.md) l’éditeur de liens.

**/LIST**<br/>
Affiche des informations sur la bibliothèque de sortie à la sortie standard. La sortie peut être redirigée vers un fichier. Vous pouvez utiliser/LIST pour déterminer le contenu d’une bibliothèque existante sans la modifier.

**/Name :** *nom_fichier*<br/>
Lors de la création d’une bibliothèque d’importation, spécifie le nom de la DLL pour laquelle la bibliothèque d’importation est générée.

**/NODEFAULTLIB**<br/>
Supprime une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’elle recherche lors de la résolution des références externes. Pour plus d’informations, consultez [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) .

**/Out :** *NomFichier*<br/>
Remplace le nom de fichier de sortie par défaut. Par défaut, la bibliothèque de sortie est créée dans le répertoire actif, avec le nom de base de la première bibliothèque ou du fichier objet sur la ligne de commande et l’extension. lib.

**/Remove :** *Object*<br/>
Omet l' *objet* spécifié de la bibliothèque de sortie. LIB crée une bibliothèque de sortie en combinant tous les objets (que ce soit dans des fichiers objets ou des bibliothèques), puis en supprimant les objets spécifiés avec/REMOVE.

**/SUBSYSTEM :**{**CONSOLE** &#124; **EFI_APPLICATION** &#124; **EFI_BOOT_SERVICE_DRIVER** &#124; **EFI_ROM** &#124; **EFI_RUNTIME_DRIVER** &#124; **Native** &#124; **POSIX** &#124; **Windows** &#124; **WindowsCE**} [, # [. # #]]<br/>
Indique au système d’exploitation comment exécuter un programme créé en établissant un lien vers la bibliothèque de sortie. Pour plus d’informations, consultez la description de l’option [/Subsystem](subsystem-specify-subsystem.md) du lien.

Les options LIB spécifiées sur la ligne de commande ne respectent pas la casse.

Vous pouvez utiliser LIB pour effectuer les tâches de gestion de bibliothèque suivantes :

- Pour ajouter des objets à une bibliothèque, spécifiez le nom de fichier de la bibliothèque existante et les noms de fichiers des nouveaux objets.

- Pour combiner des bibliothèques, spécifiez les noms de fichiers de la bibliothèque. Vous pouvez ajouter des objets et combiner des bibliothèques avec une seule commande LIB.

- Pour remplacer un membre de bibliothèque par un nouvel objet, spécifiez la bibliothèque contenant l’objet membre à remplacer et le nom de fichier du nouvel objet (ou de la bibliothèque qui le contient). Lorsqu’un objet portant le même nom existe dans plusieurs fichiers d’entrée, LIB place le dernier objet spécifié dans la commande LIB dans la bibliothèque de sortie. Lorsque vous remplacez un membre de bibliothèque, veillez à spécifier le nouvel objet ou la nouvelle bibliothèque après la bibliothèque qui contient l’ancien objet.

- Pour supprimer un membre d’une bibliothèque, utilisez l’option/REMOVE. LIB traite toutes les spécifications de/REMOVE après avoir combiné tous les objets d’entrée, indépendamment de l’ordre de la ligne de commande.

> [!NOTE]
> Vous ne pouvez pas supprimer un membre et l’extraire dans un fichier à la même étape. Vous devez d’abord extraire l’objet membre à l’aide de/EXTRACT, puis exécuter à nouveau LIB en utilisant/REMOVE. Ce comportement diffère de celui de LIB 16 bits (pour les bibliothèques OMF) fourni dans d’autres produits Microsoft.

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)
