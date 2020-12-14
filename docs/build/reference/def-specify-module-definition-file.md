---
description: En savoir plus sur:/DEF (spécifier le fichier Module-Definition)
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
ms.openlocfilehash: 3b9178004621a55f999f7c2636eaa5b697d2de98
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201701"
---
# <a name="def-specify-module-definition-file"></a>/DEF (Spécifier le fichier de définition de module)

```
/DEF:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Nom d’un fichier de définition de module (. def) à passer à l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option/DEF passe un fichier de définition de module (. def) à l’éditeur de liens. Un seul fichier. def peut être spécifié pour la liaison. Pour plus d’informations sur les fichiers. def, consultez [fichiers de définition de module](module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **entrée** .

1. Modifiez la propriété **fichier de définition de module** .

Pour spécifier un fichier. def à partir de l’environnement de développement, vous devez l’ajouter au projet avec d’autres fichiers, puis spécifier le fichier à l’option/DEF.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
