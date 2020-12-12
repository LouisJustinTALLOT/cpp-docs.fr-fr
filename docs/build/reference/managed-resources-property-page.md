---
description: 'En savoir plus sur : page de propriétés ressources managées'
title: Ressources managées (page de propriétés)
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 42816e2b4625bc5ab4620f4caafb627f55bd9cd5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190716"
---
# <a name="managed-resources-property-page"></a>Ressources managées (page de propriétés)

La page de propriétés **ressources managées** expose les propriétés suivantes pour le compilateur de ressources managées [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) lors de l’utilisation de ressources .net dans les programmes C++/CLI :

- **Nom logique de la ressource**

   Spécifie le *nom logique* du fichier .resources intermédiaire généré. Le nom logique est le nom utilisé pour charger la ressource. Si aucun nom logique n’est spécifié, le nom de fichier (.resx) de ressources est utilisé comme nom logique.

- **Nom du fichier de sortie**

   Spécifie le nom du fichier de sortie final auquel contribue le fichier (.resx) de ressources.

- **Ressources localisées par défaut**

   Spécifie si le fichier .resx donné contribue aux ressources par défaut ou à une DLL satellite.

Pour plus d’informations sur l’accès à la page de propriétés **ressources managées** , consultez [définir le compilateur C++ et les propriétés de génération dans Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[Informations de référence sur les pages de propriétés de projet C++](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (incorporer une ressource managée)](assemblyresource-embed-a-managed-resource.md)
