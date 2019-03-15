---
title: /DELAYSIGN (Signer partiellement un assembly)
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 65585b856627ad9fda5a8f8bfad6ad81fef0f81c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807648"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (Signer partiellement un assembly)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>Arguments

**NO**<br/>
Spécifie que l’assembly ne doit pas être partiellement signé.

## <a name="remarks"></a>Notes

Utilisez **/DELAYSIGN** si vous souhaitez uniquement placer la clé publique dans l’assembly. La valeur par défaut est **delaysign**.

Le **/DELAYSIGN** option est sans effet sauf si utilisée avec [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) ou [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md).

Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée. La signature numérique obtenue est stockée dans le fichier qui contient le manifeste. Lorsqu’un assembly est à signature différée, l’éditeur de liens ne calcule pas et stocker la signature, mais réserve de l’espace dans le fichier pour la signature puisse être ajoutée plus tard.

Par exemple, à l’aide de **/DELAYSIGN** permet à un testeur d’insérer l’assembly dans le cache global. Après avoir testé, vous pouvez signer complètement l’assembly en plaçant la clé privée dans l’assembly.

Consultez [les assemblys de nom fort (signature d’Assembly) (C++ / c++ / CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) et [Delay Signing an Assembly](/dotnet/framework/app-domains/delay-sign-assembly) pour plus d’informations sur la signature d’un assembly.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
