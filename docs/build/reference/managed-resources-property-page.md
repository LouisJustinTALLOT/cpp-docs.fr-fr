---
title: Ressources managées (page de propriétés)
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177528"
---
# <a name="managed-resources-property-page"></a>Ressources managées (page de propriétés)

La page de propriétés **ressources managées** expose les propriétés suivantes pour le compilateur de ressources managées [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) lors C++de l’utilisation de ressources .net dans les programmes/CLI:

- **Nom logique de la ressource**

   Spécifie le *nom logique* du fichier .resources intermédiaire généré. Le nom logique est le nom utilisé pour charger la ressource. Si aucun nom logique n’est spécifié, le nom de fichier (.resx) de ressources est utilisé comme nom logique.

- **Nom du fichier de sortie**

   Spécifie le nom du fichier de sortie final auquel contribue le fichier (.resx) de ressources.

- **Ressources localisées par défaut**

   Spécifie si le fichier .resx donné contribue aux ressources par défaut ou à une DLL satellite.

Pour plus d’informations sur la façon d’accéder à la page de propriétés **ressources managées** , consultez [définir C++ les propriétés de compilation et de génération dans Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++Référence de la page de propriétés du projet](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (Incorporer une ressource managée)](assemblyresource-embed-a-managed-resource.md)
