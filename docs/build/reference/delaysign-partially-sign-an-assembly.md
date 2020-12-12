---
description: En savoir plus sur:/DELAYSIGN (signer partiellement un assembly)
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
ms.openlocfilehash: 40eeaef958b6a188fd4739fcdc0f5ef5123b220a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201480"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (Signer partiellement un assembly)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>Arguments

**NO**<br/>
Spécifie que l’assembly ne doit pas être partiellement signé.

## <a name="remarks"></a>Notes

Utilisez **/delaysign** si vous souhaitez uniquement placer la clé publique dans l’assembly. La valeur par défaut est **/delaysign : no**.

L’option **/delaysign** n’a aucun effet, sauf si elle est utilisée avec [/keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) ou [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md).

Quand vous demandez un assembly totalement signé, le compilateur hache le fichier qui contient le manifeste (métadonnées de l’assembly) et signe ce hachage avec la clé privée. La signature numérique obtenue est stockée dans le fichier qui contient le manifeste. Lorsqu’un assembly est signé différé, l’éditeur de liens ne calcule pas et ne stocke pas la signature, mais réserve de l’espace dans le fichier pour que la signature puisse être ajoutée ultérieurement.

Par exemple, l’utilisation de la valeur **/delaysign** permet à un testeur de placer l’assembly dans le cache global. Après le test, vous pouvez signer complètement l’assembly en plaçant la clé privée dans l’assembly.

Pour plus d’informations sur la signature d’un assembly, consultez [assemblys de nom fort (signature d’assembly) (C++/CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) et [temporisation de signature d’un assembly](/dotnet/framework/app-domains/delay-sign-assembly) .

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
