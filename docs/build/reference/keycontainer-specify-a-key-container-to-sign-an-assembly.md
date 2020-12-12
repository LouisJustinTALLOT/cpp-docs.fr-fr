---
description: En savoir plus sur:/KEYCONTAINER (spécifier un conteneur de clé pour signer un assembly)
title: /KEYCONTAINER (Spécifier un conteneur de clé pour signer un assembly)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.KeyContainer
- /keycontainer
helpviewer_keywords:
- KEYCONTAINER linker option
- /KEYCONTAINER linker option
- -KEYCONTAINER linker option
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
ms.openlocfilehash: 5f32fdc5400103d4038139fa2dfe9409c9740236
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199582"
---
# <a name="keycontainer-specify-a-key-container-to-sign-an-assembly"></a>/KEYCONTAINER (Spécifier un conteneur de clé pour signer un assembly)

```
/KEYCONTAINER:name
```

## <a name="arguments"></a>Arguments

*name*<br/>
Conteneur qui contient la clé. Placez la chaîne entre guillemets doubles ("") si elle contient un espace.

## <a name="remarks"></a>Notes

L’éditeur de liens crée un assembly signé en insérant une clé publique dans le manifeste de l’assembly et en signant l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez [sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* sur la ligne de commande. **sn-i** installe la paire de clés dans un conteneur.

Si vous compilez avec [/LN](ln-create-msil-module.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly qui comprend une référence explicite au module, via [#using](../../preprocessor/hash-using-directive-cpp.md)ou lors de la liaison avec [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md).

Vous pouvez également passer vos informations de chiffrement au compilateur avec [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md). Utilisez [/delaysign](delaysign-partially-sign-an-assembly.md) si vous souhaitez obtenir un assembly partiellement signé. Pour plus d’informations sur la signature d’un assembly [, consultez assemblys de nom fort (signature d’assembly) (C++/CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) .

Les autres options de l’éditeur de liens qui affectent la génération d’assembly sont les suivantes :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

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
