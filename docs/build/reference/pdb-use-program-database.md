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
ms.openlocfilehash: ddcf83cafd5f499158f3116f04e40397b7f8d0a8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821506"
---
# <a name="pdb-use-program-database"></a>/PDB (Utiliser la base de données du programme)

```
/PDB:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Un nom spécifié par l’utilisateur pour la base de données du programme (PDB) qui crée l’éditeur de liens. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

Par défaut, lorsque [/DEBUG](debug-generate-debug-info.md) est spécifié, l’éditeur de liens crée une base de données du programme (PDB) qui contient des informations de débogage. Nom de fichier par défaut pour le fichier PDB est le nom de base du programme et l’extension .pdb.

Utilisez/PDB :*filename* pour spécifier le nom du fichier PDB. Si/Debug n’est pas spécifié, l’option /PDB est ignorée.

Un fichier PDB peut être jusqu'à 2 Go.

Pour plus d’informations, consultez [fichiers .pdb en tant qu’entrée de l’éditeur de liens](dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **déboguer** page de propriétés.

1. Modifier le **générer un fichier de base de données de programme** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
