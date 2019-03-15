---
title: /ASSEMBLYRESOURCE (Incorporer une ressource managée)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: 1eac489ffd01f6bd79fc8c5bbda23adb751c9486
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822650"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Incorporer une ressource managée)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Paramètres

*filename*<br/>
La ressource managée que vous souhaitez incorporer dans cet assembly.

*name*<br/>
Facultatif. Le nom logique de la ressource ; le nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.

Si vous le souhaitez, vous pouvez spécifier si le fichier doit être privé dans le manifeste d’assembly. Par défaut, *nom* est public dans l’assembly.

## <a name="remarks"></a>Notes

Utilisez l’option /ASSEMBLYRESOURCE pour incorporer une ressource dans un assembly.

Les ressources sont publiques dans l’assembly lors de la création avec l’éditeur de liens. L’éditeur de liens ne vous permet pas de renommer la ressource dans l’assembly.

Si *filename* est un fichier de ressources (.resources) de .NET Framework créé, par exemple, par le [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de la **System.Resources** espace de noms (consultez [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager) pour plus d’informations). Pour toutes les autres ressources, utilisez le **GetManifestResource** \* méthodes dans **System.Reflection.Assembly** classe pour accéder à la ressource au moment de l’exécution.

Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **entrée** page de propriétés.

1. Modifier le **incorporer de fichier de ressources managé** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
