---
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
ms.openlocfilehash: 7150d4ff8f35b00d96caa21fd5ea3754fec76030
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317872"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nom du fichier stub MS-DOS)

```
/STUB:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Une application MS-DOS.

## <a name="remarks"></a>Notes

L’option /STUB attache un programme stub MS-DOS à un programme de Win32.

Un programme stub est appelé si le fichier est exécuté dans MS-DOS. Il affiche généralement un message approprié ; Toutefois, n’importe quelle application MS-DOS valide peut être un programme stub.

Spécifiez un *filename* pour le programme stub après le signe deux-points ( :)) sur la ligne de commande. Les vérifications de l’éditeur de liens *filename* et émet un message d’erreur si le fichier n’est pas un fichier exécutable. Le programme doit être un fichier .exe ; un fichier .com n’est pas valide pour un programme stub.

Si cette option n’est pas utilisée, l’éditeur de liens attache un programme stub par défaut qui émet le message suivant :

```
This program cannot be run in MS-DOS mode.
```

Lors de la création d’un pilote de périphérique virtuel, *filename* permet à l’utilisateur de spécifier un nom de fichier qui contient une structure IMAGE_DOS_HEADER (définie dans WINNT. (H) à utiliser dans le VXD, plutôt que dans l’en-tête par défaut.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
