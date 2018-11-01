---
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
ms.openlocfilehash: 69cd03e029d014b9b74a8688f155dfb1f023b55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477062"
---
# <a name="managing-a-library"></a>Gestion d'une bibliothèque

Le mode par défaut pour LIB consiste à créer ou modifier une bibliothèque d’objets COFF. LIB s’exécute dans ce mode lorsque vous ne spécifiez pas /EXTRACT (pour copier un objet dans un fichier) ou /DEF (pour créer une bibliothèque d’importation).

Pour générer une bibliothèque à partir d’objets et/ou de bibliothèques, utilisez la syntaxe suivante :

```
LIB [options...] files...
```

Cette commande crée une bibliothèque à partir d’un ou plusieurs entrées *fichiers*. Le *fichiers* peuvent être des fichiers objets COFF, des fichiers d’objets OMF 32 bits ou des bibliothèques COFF existantes. LIB crée une bibliothèque qui contient tous les objets dans les fichiers spécifiés. Si un fichier d’entrée est un fichier d’objet OMF 32 bits, LIB le convertit au format COFF avant de générer la bibliothèque. LIB ne peut pas accepter un objet OMF 32 bits qui se trouve dans une bibliothèque créée par la version 16 bits de LIB. Vous devez d’abord utiliser la bibliothèque de 16 bits pour extraire l’objet ; Vous pouvez ensuite utiliser le fichier objet extrait comme entrée pour la bibliothèque de 32 bits.

Par défaut, LIB nomme le fichier de sortie en utilisant le nom de base du premier fichier objet ou bibliothèque et l’extension. lib. Le fichier de sortie est placé dans le répertoire actif. Si un fichier existe déjà avec le même nom, le fichier de sortie remplace le fichier existant. Pour conserver une bibliothèque existante, utilisez l’option /OUT pour spécifier un nom pour le fichier de sortie.

Les options suivantes s’appliquent à la création et modification d’une bibliothèque :

**/ LIBPATH :** *dir*<br/>
Substitue le chemin d’accès de la bibliothèque d’environnement. Pour plus d’informations, consultez la description du lien [/LIBPATH](../../build/reference/libpath-additional-libpath.md) option.

**/ LISTE**<br/>
Affiche des informations sur la bibliothèque de sortie vers la sortie standard. La sortie peut être redirigée vers un fichier. Vous pouvez utiliser /LIST pour déterminer le contenu d’une bibliothèque existante sans le modifier.

**/ NAME :** *nom de fichier*<br/>
Lorsque vous créez une bibliothèque d’importation, spécifie le nom de la DLL pour laquelle la bibliothèque d’importation est générée.

**/NODEFAULTLIB**<br/>
Supprime une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’elle parcourt lors de la résolution des références externes. Consultez [/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md) pour plus d’informations.

**/ OUT :** *nom de fichier*<br/>
Remplace le nom de fichier de sortie par défaut. Par défaut, la bibliothèque de sortie est créée dans le répertoire actif, avec le nom de base du premier fichier de bibliothèque ou un objet sur la ligne de commande et l’extension. lib.

**/ REMOVE :** *objet*<br/>
Omet spécifié *objet* à partir de la bibliothèque de sortie. LIB crée une bibliothèque de sortie en combinant tous les objets (que ce soit dans les fichiers objets ou bibliothèques), puis supprimez tous les objets spécifiés avec /Remove.

**/ SOUS-SYSTÈME :**{**CONSOLE** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM** &AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **NATIF** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [, #[. ##]]<br/>
Indique le système d’exploitation comment exécuter un programme créé par la liaison à la bibliothèque de sortie. Pour plus d’informations, consultez la description du lien [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) option.

Les options LIB spécifiées sur la ligne de commande ne respectent pas la casse.

Vous pouvez utiliser LIB pour effectuer les tâches de gestion de bibliothèque suivantes :

- Pour ajouter des objets dans une bibliothèque, spécifiez le nom de fichier de la bibliothèque existante et les noms de fichiers pour les nouveaux objets.

- Pour combiner des bibliothèques, spécifiez les noms de fichier de bibliothèque. Vous pouvez ajouter des objets et combiner des bibliothèques avec une seule commande LIB.

- Pour remplacer un membre de bibliothèque avec un nouvel objet, spécifiez la bibliothèque contenant l’objet membre à remplacer et le nom de fichier pour le nouvel objet (ou la bibliothèque qui le contient). Lorsqu’un objet qui porte le même nom existe dans plusieurs fichiers d’entrée, LIB place le dernier objet spécifié dans la commande LIB dans la bibliothèque de sortie. Lorsque vous remplacez un membre de bibliothèque, veillez à spécifier le nouvel objet ou la bibliothèque après la bibliothèque qui contient l’ancien objet.

- Pour supprimer un membre d’une bibliothèque, utilisez l’option /REMOVE. LIB traite les spécifications de /REMOVE après avoir combiné tous les objets d’entrée, indépendamment de l’ordre de ligne de commande.

> [!NOTE]
>  Vous ne peut pas à la fois supprimer un membre et l’extraire vers un fichier dans la même étape. Vous devez d’abord extraire l’objet membre à l’aide de /EXTRACT, puis exécuter LIB à nouveau à l’aide / Remove. Ce comportement diffère de celui de la version 16 bits LIB (pour les bibliothèques OMF) fournie dans d’autres produits Microsoft.

## <a name="see-also"></a>Voir aussi

[Référence LIB](../../build/reference/lib-reference.md)