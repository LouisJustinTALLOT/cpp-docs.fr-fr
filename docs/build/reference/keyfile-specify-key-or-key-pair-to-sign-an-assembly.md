---
description: En savoir plus sur:/KEYFILE (spécifier une clé ou une paire de clés pour signer un assembly)
title: /KEYFILE (Spécifier une clé ou une paire de clés pour signer un assembly)
ms.date: 11/04/2016
f1_keywords:
- /keyfile
- VC.Project.VCLinkerTool.KeyFile
helpviewer_keywords:
- /KEYFILE linker option
- -KEYFILE linker option
- KEYFILE linker option
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
ms.openlocfilehash: 23c4962ab57688f5d8c1af27fd412d7d36be01a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191158"
---
# <a name="keyfile-specify-key-or-key-pair-to-sign-an-assembly"></a>/KEYFILE (Spécifier une clé ou une paire de clés pour signer un assembly)

```
/KEYFILE:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Fichier qui contient la clé. Placez la chaîne entre guillemets doubles ("") si elle contient un espace.

## <a name="remarks"></a>Notes

L’éditeur de liens insère la clé publique dans le manifeste de l’assembly, puis signe l’assembly final avec la clé privée. Pour générer un fichier de clé, tapez [sn-k](/dotnet/framework/tools/sn-exe-strong-name-tool) *filename* sur la ligne de commande. Un assembly signé est dit avoir un nom fort.

Si vous compilez avec [/LN](ln-create-msil-module.md), le nom du fichier de clé est conservé dans le module et incorporé dans l’assembly créé quand vous compilez un assembly qui comprend une référence explicite au module, via [#using](../../preprocessor/hash-using-directive-cpp.md)ou lors de la liaison avec [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md).

Vous pouvez également passer vos informations de chiffrement à l’éditeur de liens avec [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md). Utilisez [/delaysign](delaysign-partially-sign-an-assembly.md) si vous souhaitez obtenir un assembly partiellement signé. Pour plus d’informations sur la signature d’un assembly [, consultez assemblys de nom fort (signature d’assembly) (C++/CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) .

Si **/keyfile** et **/keycontainer** sont spécifiés (par option de ligne de commande ou par attribut personnalisé), l’éditeur de liens essaie d’abord d’utiliser le conteneur de clé. Si cette tentative réussit, l'assembly est signé avec les informations figurant dans le conteneur de clé. Si l’éditeur de liens ne trouve pas le conteneur de clé, il essaie d’utiliser le fichier spécifié avec/KEYFILE. En cas de réussite, l'assembly est signé avec les informations du fichier de clé et les informations sur la clé sont installées dans le conteneur de clé (semblable à sn -i) de sorte qu'à la compilation suivante, le conteneur de clé est valide.

Notez qu’un fichier de clé peut contenir uniquement la clé publique.

Pour plus d’informations sur la signature d’un assembly [, consultez Création et utilisation d’assemblys Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies) .

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
