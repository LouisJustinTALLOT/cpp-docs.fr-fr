---
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
ms.openlocfilehash: fb707a2721ed40ee3ec37d01b2bbcfcc51f05c38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295160"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Fichier de ressources .NET Framework que vous voulez lier à l’assembly.

## <a name="remarks"></a>Notes

L’option /ASSEMBLYLINKRESOURCE crée un lien vers une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie. [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) incorpore un fichier de ressources dans le fichier de sortie.

Les ressources liées sont publiques dans l’assembly lors de la création avec l’éditeur de liens.

/ASSEMBLYLINKRESOURCE impose que la compilation inclue [/CLR](clr-common-language-runtime-compilation.md); [/LN](ln-create-msil-module.md) ou [/NOASSEMBLY](noassembly-create-a-msil-module.md) n’est pas autorisée avec /ASSEMBLYLINKRESOURCE.

Si *filename* est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de la **System.Resources** espace de noms. Pour plus d’informations, consultez [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager). Pour toutes les autres ressources, utilisez le **GetManifestResource** \* méthodes dans le **System.Reflection.Assembly** classe pour accéder à la ressource au moment de l’exécution.

*nom de fichier* peut être n’importe quel format de fichier. Par exemple, vous souhaiterez effectuer une DLL native fasse partie de l’assembly, afin de pouvoir être installé dans le Global Assembly Cache et accessible à partir de code managé dans l’assembly.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l’option dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
