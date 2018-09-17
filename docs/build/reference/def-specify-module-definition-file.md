---
title: -DEF (spécifier un fichier de définition de Module) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
dev_langs:
- C++
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ec7458f5b81dd2b9d5aac49959b935f49377081
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720393"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Spécifier le fichier de définition de module)

```
/DEF:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Le nom d’un fichier de définition de module (.def) à passer à l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option /DEF passe un fichier de définition de module (.def) à l’éditeur de liens. Un seul fichier .def peut être spécifié au lien. Pour plus d’informations sur les fichiers .def, consultez [les fichiers de définition de Module](../../build/reference/module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **fichier de définition de Module** propriété.

Pour spécifier un fichier .def dans l’environnement de développement, vous devez l’ajouter au projet, ainsi que d’autres fichiers et spécifiez ensuite le fichier à l’option /DEF.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)