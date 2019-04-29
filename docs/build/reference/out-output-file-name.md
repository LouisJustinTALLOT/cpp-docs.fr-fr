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
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320069"
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

Cette option le nom de base par défaut pour une bibliothèque de fichier de mappage ou d’importation. Pour plus d’informations, consultez [générer fichier de mappage](map-generate-mapfile.md) (/Map) et [/IMPLIB](implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **général** page de propriétés.

1. Modifier le **fichier de sortie** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
