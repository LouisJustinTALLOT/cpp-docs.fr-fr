---
description: En savoir plus sur:/ASSEMBLYLINKRESOURCE (lien vers la ressource .NET Framework)
title: /ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)
ms.date: 11/04/2016
f1_keywords:
- /ASSEMBLYLINKRESOURCE
- VC.Project.VCLinkerTool.AssemblyLinkResource
helpviewer_keywords:
- -ASSEMBLYLINKRESOURCE linker option
- ASSEMBLYLINKRESOURCE linker option
- /ASSEMBLYLINKRESOURCE linker option
ms.assetid: 8b6ad184-1b33-47a4-8513-4803cf915b64
ms.openlocfilehash: 32761cb16e8428d5e3c18330dffb49a50a42903c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183007"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>Arguments

*extension*<br/>
Fichier de ressources .NET Framework que vous voulez lier à l’assembly.

## <a name="remarks"></a>Notes

L’option/ASSEMBLYLINKRESOURCE crée un lien vers une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie. [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) incorpore un fichier de ressources dans le fichier de sortie.

Les ressources liées sont publiques dans l’assembly quand elles sont créées avec l’éditeur de liens.

/ASSEMBLYLINKRESOURCE requiert que la compilation inclue [/CLR](clr-common-language-runtime-compilation.md); [/LN](ln-create-msil-module.md) ou [/noAssembly](noassembly-create-a-msil-module.md) n’est pas autorisé avec/ASSEMBLYLINKRESOURCE.

Si *filename* est un fichier de ressources de .NET Framework créé, par exemple, par [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de l’espace de noms **System. Resources** . Pour plus d’informations, consultez [System. resources. ResourceManager](/dotnet/api/system.resources.resourcemanager). Pour toutes les autres ressources, utilisez les méthodes **GetManifestResource** \* de la classe **System. Reflection. assembly** pour accéder à la ressource au moment de l’exécution.

*filename* peut être n’importe quel format de fichier. Par exemple, vous souhaiterez peut-être créer une DLL native de l’assembly, afin qu’elle puisse être installée dans le global assembly cache et accessible à partir du code managé dans l’assembly.

Les autres options de l’éditeur de liens qui affectent la génération d’assembly sont les suivantes :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

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
