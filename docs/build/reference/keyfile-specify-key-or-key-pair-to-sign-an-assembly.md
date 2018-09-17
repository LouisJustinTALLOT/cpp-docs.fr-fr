---
title: -KEYFILE (spécifier la clé ou une paire de clés pour signer un Assembly) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
dev_langs:
- C++
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f43609e14d4e081f39c43cb8e548b8b6ac7923a1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701272"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Spécifier une clé ou une paire de clés pour signer un assembly)

```
/KEYFILE:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Fichier qui contient la clé. Placez la chaîne entre guillemets doubles ( » «) s’il contient un espace.

## <a name="remarks"></a>Notes

L’éditeur de liens insère la clé publique dans le manifeste d’assembly et puis signe l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez [sn -k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* en ligne de commande. Un assembly signé est dite avoir un nom fort.

Si vous compilez avec [/LN](../../build/reference/ln-create-msil-module.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly qui est créé lorsque vous compilez un assembly qui inclut une référence explicite au module, via [#using](../../preprocessor/hash-using-directive-cpp.md), ou lors de la liaison avec [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md).

Vous pouvez également passer vos informations de chiffrement à l’éditeur de liens avec [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md). Utilisez [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md) si vous souhaitez obtenir un assembly partiellement signé. Consultez [les assemblys de nom fort (signature d’Assembly) (C++ / c++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) pour plus d’informations sur la signature d’un assembly.

Tous deux **/keyfile** et **/KEYCONTAINER** sont spécifiés (par option de ligne de commande ou par attribut personnalisé), l’éditeur de liens tente d’abord le conteneur de clé. Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé. Si l’éditeur de liens ne trouve pas le conteneur de clé, il essaie le fichier spécifié avec /KEYFILE. En cas de réussite, l'assembly est signé avec les informations du fichier de clé et les informations sur la clé sont installées dans le conteneur de clé (semblable à sn -i) de sorte qu'à la compilation suivante, le conteneur de clé est valide.

Notez qu’un fichier de clé peut contenir uniquement la clé publique.

Consultez [création et assemblys avec nom fort](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) pour plus d’informations sur la signature d’un assembly.

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