---
title: -/ASSEMBLYRESOURCE (incorporer une ressource managée) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
dev_langs:
- C++
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88afe292905ee46c1e939d29f787055f98058dc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (Incorporer une ressource managée)
```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## <a name="parameters"></a>Paramètres  
 *filename*  
 La ressource managée que vous souhaitez incorporer dans cet assembly.  
  
 *name*  
 Facultatif. Le nom logique de la ressource ; le nom utilisé pour charger la ressource. La valeur par défaut est le nom du fichier.  
  
 Si vous le souhaitez, vous pouvez spécifier si le fichier doit être privé dans le manifeste d’assembly. Par défaut, *nom* est public dans l’assembly.  
  
## <a name="remarks"></a>Notes  
 Utilisez l’option /ASSEMBLYRESOURCE pour incorporer une ressource dans un assembly.  
  
 Les ressources sont publiques dans l’assembly lorsqu’elles sont créées avec l’éditeur de liens. L’éditeur de liens ne vous permet pas de renommer la ressource dans l’assembly.  
  
 Si *nom de fichier* est un fichier de ressources (.resources) de .NET Framework créé, par exemple, par le [Resource File Generator (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou dans l’environnement de développement, il est accessible à l’aide des membres de la **System.Resources** espace de noms (consultez [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx) pour plus d’informations). Pour toutes les autres ressources, utilisez le **GetManifestResource** \* méthodes dans **System.Reflection.Assembly** classe pour accéder à la ressource au moment de l’exécution.  
  
 Autres options de l’éditeur de liens qui affectent la génération de l’assembly sont :  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [définition des propriétés de projet Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le **l’éditeur de liens** dossier.  
  
3.  Cliquez sur le **entrée** page de propriétés.  
  
4.  Modifier la **incorporer de fichier de ressources managé** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)