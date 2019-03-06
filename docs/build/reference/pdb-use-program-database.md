---
title: /PDB (Utiliser la base de données du programme)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: 6a57e4eb23d40355094f4c8274a42ccb7e1b0e20
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420633"
---
# <a name="pdb-use-program-database"></a>/PDB (Utiliser la base de données du programme)

```
/PDB:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Un nom spécifié par l’utilisateur pour la base de données du programme (PDB) qui crée l’éditeur de liens. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

Par défaut, lorsque [/DEBUG](../../build/reference/debug-generate-debug-info.md) est spécifié, l’éditeur de liens crée une base de données du programme (PDB) qui contient des informations de débogage. Nom de fichier par défaut pour le fichier PDB est le nom de base du programme et l’extension .pdb.

Utilisez/PDB :*filename* pour spécifier le nom du fichier PDB. Si/Debug n’est pas spécifié, l’option /PDB est ignorée.

Un fichier PDB peut être jusqu'à 2 Go.

Pour plus d’informations, consultez [fichiers .pdb en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modifier le **générer un fichier de base de données de programme** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
