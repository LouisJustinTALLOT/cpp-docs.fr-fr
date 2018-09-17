---
title: -KEYCONTAINER (spécifier un conteneur de clé pour signer un Assembly) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
dev_langs:
- C++
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 850a8173dba3e69eaf52fdf174674e1dba58a4d8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723760"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Spécifier un conteneur de clé pour signer un assembly)

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>Arguments

*name*<br/>
Conteneur qui contient la clé. Placez la chaîne entre guillemets doubles ( » «) s’il contient un espace.

## <a name="remarks"></a>Notes

L’éditeur de liens crée un assembly signé en insérant une clé publique dans le manifeste d’assembly et en signant l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* en ligne de commande. **sn -i** installe la paire de clés dans un conteneur.

Si vous compilez avec [/LN](../../build/reference/ln-create-msil-module.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly qui est créé lorsque vous compilez un assembly qui inclut une référence explicite au module, via [#using](../../preprocessor/hash-using-directive-cpp.md), ou lors de la liaison avec [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).

Vous pouvez également passer vos informations de chiffrement au compilateur avec [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Utilisez [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) si vous souhaitez obtenir un assembly partiellement signé. Consultez [les assemblys de nom fort (signature d’Assembly) (C++ / c++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) pour plus d’informations sur la signature d’un assembly.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)