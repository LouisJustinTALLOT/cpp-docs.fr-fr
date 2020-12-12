---
description: En savoir plus sur:/ASSEMBLYRESOURCE (incorporer une ressource managée)
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
ms.openlocfilehash: 3f79cc177df72bb83288a0a229fdf47adb0e7fc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182916"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Incorporer une ressource managée)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Paramètres

*filename*<br/>
Ressource managée que vous souhaitez incorporer dans cet assembly.

*name*<br/>
facultatif. Nom logique de la ressource ; nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.

Si vous le souhaitez, vous pouvez spécifier si le fichier doit être privé dans le manifeste de l’assembly. Par défaut, le *nom* est public dans l’assembly.

## <a name="remarks"></a>Notes

Utilisez l’option/ASSEMBLYRESOURCE pour incorporer une ressource dans un assembly.

Les ressources sont publiques dans l’assembly quand elles sont créées avec l’éditeur de liens. L’éditeur de liens ne vous permet pas de renommer la ressource dans l’assembly.

Si *filename* est un fichier de ressources de .NET Framework (. Resources) créé, par exemple, par le [Générateur de fichiers de ressources (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de l’espace de noms **System. Resources** (pour plus d’informations, consultez [System. resources. ResourceManager](/dotnet/api/system.resources.resourcemanager) ). Pour toutes les autres ressources, utilisez les méthodes **GetManifestResource** \* de la classe **System. Reflection. assembly** pour accéder à la ressource au moment de l’exécution.

Les autres options de l’éditeur de liens qui affectent la génération d’assembly sont les suivantes :

- [/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **entrée** .

1. Modifiez la propriété **incorporer le fichier de ressources managées** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
