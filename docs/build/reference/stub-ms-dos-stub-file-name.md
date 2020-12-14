---
description: En savoir plus sur:/STUB (nom du fichier stub MS-DOS)
title: /STUB (Nom du fichier stub MS-DOS)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: 34f3cd71ce66cb6695a58707fd84de79f7a14b1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230300"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nom du fichier stub MS-DOS)

```
/STUB:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Une application MS-DOS.

## <a name="remarks"></a>Notes

L’option/STUB attache un programme stub MS-DOS à un programme Win32.

Un programme stub est appelé si le fichier est exécuté dans MS-DOS. Il affiche généralement un message approprié. Toutefois, toute application MS-DOS valide peut être un programme stub.

Spécifiez un *nom de fichier* pour le programme stub après un signe deux-points ( :) sur la ligne de commande. L’éditeur de liens vérifie *filename* et émet un message d’erreur si le fichier n’est pas un fichier exécutable. Le programme doit être un fichier. exe ; un fichier. com n’est pas valide pour un programme stub.

Si cette option n’est pas utilisée, l’éditeur de liens attache un programme stub par défaut qui émet le message suivant :

```
This program cannot be run in MS-DOS mode.
```

Lors de la création d’un pilote de périphérique virtuel, *filename* permet à l’utilisateur de spécifier un nom de fichier qui contient une structure IMAGE_DOS_HEADER (définie dans Winnt. H) à utiliser dans le VXD, plutôt que dans l’en-tête par défaut.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans la zone **options supplémentaires** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
