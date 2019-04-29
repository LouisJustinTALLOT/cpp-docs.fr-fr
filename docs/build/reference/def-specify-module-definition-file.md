---
title: /DEF (Spécifier le fichier de définition de module)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: c08412fb50835485e7941b2bb1db088943387b71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272306"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Spécifier le fichier de définition de module)

```
/DEF:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Le nom d’un fichier de définition de module (.def) à passer à l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option /DEF passe un fichier de définition de module (.def) à l’éditeur de liens. Un seul fichier .def peut être spécifié au lien. Pour plus d’informations sur les fichiers .def, consultez [les fichiers de définition de Module](module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **fichier de définition de Module** propriété.

Pour spécifier un fichier .def dans l’environnement de développement, vous devez l’ajouter au projet, ainsi que d’autres fichiers et spécifiez ensuite le fichier à l’option /DEF.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
