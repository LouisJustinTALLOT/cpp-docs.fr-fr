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
ms.openlocfilehash: 7c1d78758e43bf8e0c2c281c495c81e9f62b36e7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473903"
---
# <a name="assemblylinkresource-link-to-net-framework-resource"></a>/ASSEMBLYLINKRESOURCE (Lien vers une ressource du .NET Framework)

```
/ASSEMBLYLINKRESOURCE:filename
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Fichier de ressources .NET Framework que vous voulez lier à l’assembly.

## <a name="remarks"></a>Notes

L’option /ASSEMBLYLINKRESOURCE crée un lien vers une ressource .NET Framework dans le fichier de sortie ; le fichier de ressources n’est pas placé dans le fichier de sortie. [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md) incorpore un fichier de ressources dans le fichier de sortie.

Les ressources liées sont publiques dans l’assembly lors de la création avec l’éditeur de liens.

/ASSEMBLYLINKRESOURCE impose que la compilation inclue [/CLR](../../build/reference/clr-common-language-runtime-compilation.md); [/LN](../../build/reference/ln-create-msil-module.md) ou [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md) n’est pas autorisée avec /ASSEMBLYLINKRESOURCE.

Si *filename* est un fichier de ressources .NET Framework créé, par exemple, par [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de la **System.Resources** espace de noms. Pour plus d’informations, consultez [System.Resources.ResourceManager](https://msdn.microsoft.com/library/system.resources.resourcemanager.aspx). Pour toutes les autres ressources, utilisez le **GetManifestResource** \* méthodes dans le **System.Reflection.Assembly** classe pour accéder à la ressource au moment de l’exécution.

*nom de fichier* peut être n’importe quel format de fichier. Par exemple, vous souhaiterez effectuer une DLL native fasse partie de l’assembly, afin de pouvoir être installé dans le Global Assembly Cache et accessible à partir de code managé dans l’assembly.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

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