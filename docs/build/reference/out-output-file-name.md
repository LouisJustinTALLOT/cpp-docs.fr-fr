---
description: En savoir plus sur:/OUT (nom du fichier de sortie)
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
ms.openlocfilehash: 1773b4b2dd340bc105495c1b05211c018548976f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226400"
---
# <a name="out-output-file-name"></a>/OUT (Nom du fichier de sortie)

```
/OUT:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Nom spécifié par l’utilisateur pour le fichier de sortie. Il remplace le nom par défaut.

## <a name="remarks"></a>Notes

L’option/OUT substitue le nom et l’emplacement par défaut du programme créé par l’éditeur de liens.

Par défaut, l’éditeur de liens forme le nom de fichier à l’aide du nom de base du premier fichier. obj spécifié et de l’extension appropriée (. exe ou. dll).

Cette option permet d’obtenir le nom de base par défaut d’une bibliothèque de mappage ou d’importation. Pour plus d’informations, consultez [générer un mappage](map-generate-mapfile.md) (/Map) et [/IMPLIB](implib-name-import-library.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **général** .

1. Modifiez la propriété **fichier de sortie** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
