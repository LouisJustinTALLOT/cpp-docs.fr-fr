---
title: -PDB (base de données de programme utilisation) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
dev_langs:
- C++
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8717be9ee8f754f4e61dbed0211360a0b4f4f780
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717232"
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