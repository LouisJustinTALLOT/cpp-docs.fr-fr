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
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336408"
---
# <a name="managing-a-library"></a>Gestion d'une bibliothèque

Le mode par défaut pour LIB est de construire ou de modifier une bibliothèque d’objets COFF. LIB fonctionne dans ce mode lorsque vous ne spécifiez pas /EXTRACT (pour copier un objet à un fichier) ou /DEF (pour construire une bibliothèque d’importation).

Pour construire une bibliothèque à partir d’objets et/ou de bibliothèques, utilisez la syntaxe suivante :

```
LIB [options...] files...
```

Cette commande crée une bibliothèque à partir d’un ou plusieurs *fichiers*d’entrée . Les *fichiers* peuvent être des fichiers d’objets COFF, des fichiers d’objets OMF 32 bits ou des bibliothèques COFF existantes. LIB crée une bibliothèque qui contient tous les objets dans les fichiers spécifiés. Si un fichier d’entrée est un fichier d’objets OMF 32 bits, LIB le convertit en COFF avant de construire la bibliothèque. LIB ne peut pas accepter un objet OMF 32 bits qui se trouve dans une bibliothèque créée par la version 16 bits de LIB. Vous devez d’abord utiliser le LIB 16 bits pour extraire l’objet; alors vous pouvez utiliser le fichier d’objet extrait comme entrée sur le LIB 32 bits.

Par défaut, LIB nomme le fichier de sortie en utilisant le nom de base du premier fichier d’objet ou de bibliothèque et l’extension .lib. Le fichier de sortie est mis dans l’annuaire actuel. Si un fichier existe déjà du même nom, le fichier de sortie remplace le fichier existant. Pour préserver une bibliothèque existante, utilisez l’option /OUT pour spécifier un nom pour le fichier de sortie.

Les options suivantes s’appliquent à la construction et à la modification d’une bibliothèque :

**/LIBPATH:** *dir*<br/>
Substitue le chemin d’accès de la bibliothèque d’environnement. Pour plus de détails, consultez la description de l’option [LINK/LIBPATH.](libpath-additional-libpath.md)

**/LISTE**<br/>
Affiche des informations sur la bibliothèque de sortie à la sortie standard. La sortie peut être redirigée vers un fichier. Vous pouvez utiliser /LIST pour déterminer le contenu d’une bibliothèque existante sans la modifier.

**/NAME:** *nom de fichier*<br/>
Lors de la construction d’une bibliothèque d’importation, précise le nom de la DLL pour laquelle la bibliothèque d’importation est en cours de construction.

**/NODEFAULTLIB**<br/>
Supprime une ou plusieurs bibliothèques par défaut de la liste des bibliothèques qu’elle recherche lors de la résolution de références externes. Voir [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) pour plus d’informations.

**/OUT:** *nom de fichier*<br/>
Remplace le nom de fichier de sortie par défaut. Par défaut, la bibliothèque de sortie est créée dans l’annuaire actuel, avec le nom de base de la première bibliothèque ou fichier d’objets sur la ligne de commande et l’extension .lib.

**/SUPPRIMER:** *objet*<br/>
Omet *l’objet* spécifié à partir de la bibliothèque de sortie. LIB crée une bibliothèque de sortie en combinant tous les objets (que ce soit dans les fichiers d’objets ou les bibliothèques), puis en supprimant tous les objets spécifiés avec /REMOVE.

**/SUBSYSTEM:**'**CONSOLE** &#124; **EFI_APPLICATION** **&#124; EFI_BOOT_SERVICE_DRIVER** &#124; **EFI_ROM** **&#124; EFI_RUNTIME_DRIVER** &#124; **NATIVE** &#124; **POSIX** &#124; **WINDOWS** &#124; **WINDOWSCE**'[.]]<br/>
Indique au système d’exploitation comment exécuter un programme créé en reliant à la bibliothèque de sortie. Pour plus d’informations, consultez la description de l’option [LINK/SUBSYSTEM.](subsystem-specify-subsystem.md)

Les options LIB spécifiées sur la ligne de commande ne sont pas sensibles aux cas.

Vous pouvez utiliser LIB pour effectuer les tâches suivantes de gestion de bibliothèque :

- Pour ajouter des objets à une bibliothèque, spécifiez le nom de fichier de la bibliothèque existante et les noms de fichiers pour les nouveaux objets.

- Pour combiner les bibliothèques, spécifiez les noms de fichiers de la bibliothèque. Vous pouvez ajouter des objets et combiner des bibliothèques avec une seule commande LIB.

- Pour remplacer un membre de la bibliothèque par un nouvel objet, spécifiez la bibliothèque contenant l’objet membre à remplacer et le nom de fichier du nouvel objet (ou la bibliothèque qui le contient). Lorsqu’un objet qui porte le même nom existe dans plus d’un fichier d’entrée, LIB met le dernier objet spécifié dans la commande LIB dans la bibliothèque de sortie. Lorsque vous remplacez un membre de la bibliothèque, assurez-vous de spécifier le nouvel objet ou bibliothèque après la bibliothèque qui contient l’ancien objet.

- Pour supprimer un membre d’une bibliothèque, utilisez l’option /REMOVE. LIB traite toutes les spécifications de /REMOVE après avoir combiné tous les objets d’entrée, quel que soit l’ordre de commande.

> [!NOTE]
> Vous ne pouvez pas supprimer un membre et l’extraire dans un fichier dans la même étape. Vous devez d’abord extraire l’objet membre à l’aide de /EXTRACT, puis exécuter LIB à nouveau en utilisant /REMOVE. Ce comportement diffère de celui du LIB 16 bits (pour les bibliothèques OMF) fourni dans d’autres produits Microsoft.

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)
