---
title: /OUT (Nom du fichier de sortie)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: f5ba323b830b9d06956d88d957206e3f73c15418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497177"
---
# <a name="out-output-file-name"></a>/OUT (Nom du fichier de sortie)

```
/OUT:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Nom du fichier de sortie spécifié par l’utilisateur. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

L’option /OUT substitue le nom par défaut et l’emplacement du programme qui crée l’éditeur de liens.

Par défaut, l’éditeur de liens constitue le nom de fichier en utilisant le nom de base du premier fichier .obj spécifié et l’extension appropriée (.exe ou .dll).

Cette option le nom de base par défaut pour une bibliothèque de fichier de mappage ou d’importation. Pour plus d’informations, consultez [générer fichier de mappage](../../build/reference/map-generate-mapfile.md) (/Map) et [/IMPLIB](../../build/reference/implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **général** page de propriétés.

1. Modifier le **fichier de sortie** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)