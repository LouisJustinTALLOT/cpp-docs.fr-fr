---
description: En savoir plus sur:/PDB (utiliser la base de données du programme)
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
ms.openlocfilehash: 221d5d81dc3578e99751334b2e0a0a61aaaed356
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226101"
---
# <a name="pdb-use-program-database"></a>/PDB (Utiliser la base de données du programme)

```
/PDB:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Nom spécifié par l’utilisateur pour la base de données du programme (PDB) créée par l’éditeur de liens. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

Par défaut, quand [/Debug](debug-generate-debug-info.md) est spécifié, l’éditeur de liens crée une base de données de programme (PDB) qui contient des informations de débogage. Le nom de fichier par défaut pour le fichier PDB porte le nom de base du programme et l’extension. pdb.

Utilisez/PDB :*filename* pour spécifier le nom du fichier PDB. Si/DEBUG n’est pas spécifié, l’option/PDB est ignorée.

Un fichier PDB peut atteindre 2 Go.

Pour plus d’informations, consultez [fichiers. pdb en tant qu’entrée dans l’éditeur de liens](dot-pdb-files-as-linker-input.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Déboguer** .

1. Modifiez la propriété **générer le fichier de base de données du programme** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
