---
title: Pages de propriétés de l’éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCLinkerTool.RegisterOutput
- VC.Project.VCLinkerTool.OVERWRITEImportLibrary
- VC.Project.VCLinkerTool.UseLibraryDependencyInputs
- VC.Project.VCLinkerTool.LinkLibraryDependencies
dev_langs:
- C++
helpviewer_keywords:
- per-user redirection
- Linker property pages
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cec232bb4e4f2f6ac1ab9af703b368eec0ba5dd
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331517"
---
# <a name="linker-property-pages"></a>pages de propriétés de l'Éditeur de liens

Cette rubrique décrit les propriétés suivantes de la page de propriétés **Général** de l’éditeur de liens. Pour obtenir la version Linux de cette page, consultez [Éditeur de liens, propriétés (Linux C++)](../linux/prop-pages/linker-linux.md).

## <a name="general-page-properties"></a>Propriétés de la page Général

### <a name="ignore-import-library"></a>Bibliothèque d’importation ignorée

Cette propriété indique à l’éditeur de liens ne pas lier de sortie .lib générée à partir de cette build dans n’importe quel projet dépendant. Vous autorisez ainsi le système de projet à gérer les fichiers .dll qui ne créent pas de fichier .lib lors de la génération. Si un projet dépend d’un autre projet créant une DLL, le système de projet lie automatiquement le fichier .lib produit par ce projet enfant. Il se peut que cette propriété ne soit pas nécessaire pour les projets créant des DLL COM ou des DLL de ressource uniquement. En effet, ces DLL ne possèdent pas d’exportation significative. Si une DLL ne possède aucune exportation, l’éditeur de liens ne crée pas de fichier .lib. Si aucun fichier .lib d’exportation n’est présent sur le disque et si le système de projet indique à l’éditeur de liens d’établir la liaison à cette DLL (manquante), la liaison échoue. Utilisez la propriété **Bibliothèque d’importation ignorée** pour résoudre ce problème. Si elle a la valeur **Oui**, le système de projet ignore la présence ou l’absence de ce fichier .lib et empêche la liaison d’un projet dépendant de ce projet au fichier .lib manquant.

Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Inscription de la sortie

Exécute `regsvr32.exe /s $(TargetPath)` sur la sortie de génération, qui est valide uniquement sur les projets .dll. Pour les projets .exe, cette propriété est ignorée. Pour inscrire un fichier de sortie .exe, définissez un événement post-build dans la configuration afin d’effectuer l’inscription personnalisée obligatoire pour les fichiers .exe inscrits.

Pour accéder par programmation à cette propriété, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Redirection par utilisateur

L’inscription dans Visual Studio s’effectue traditionnellement dans HKEY_CLASSES_ROOT (HKCR). Avec Windows Vista et les systèmes d’exploitation ultérieurs, vous devez exécuter Visual Studio en mode élevé pour accéder à HKCR. Les développeurs ne souhaitent pas toujours exécuter l’application en mode élevé, mais sont toujours obligés de s’inscrire. La redirection par utilisateur vous permet de vous inscrire sans avoir à exécuter ce mode.

La redirection par utilisateur force toutes les écritures dans HKCR à être redirigées vers HKEY\_CURRENT\_USER (HKCU). Si la redirection par utilisateur est désactivée, [Erreur de génération de projet PRJ0050](../error-messages/tool-errors/project-build-error-prj0050.md) peut survenir quand le programme essaie d’écrire dans HKCR.

### <a name="link-library-dependencies"></a>Lier les dépendances de la bibliothèque

Indique s’il convient de lier les fichiers .lib produits par les projets dépendants. En règle générale, vous souhaitez lier les fichiers .lib, mais cela peut ne pas être le cas pour certaines DLL.

Vous pouvez également spécifier un fichier .obj en fournissant le nom de fichier et le chemin relatif, par exemple « ..\\..\MyLibProject\MyObjFile.obj ». Si le code source du fichier .obj inclut (#include) un en-tête précompilé, par exemple pch.h, le fichier pch.obj est situé dans le même dossier que MyObjFile.obj et vous devez également ajouter pch.obj comme dépendance supplémentaire.

### <a name="use-library-dependency-inputs"></a>Utiliser les entrées de dépendance de la bibliothèque

Dans un grand projet, quand un projet dépendant produit un fichier .lib, la liaison incrémentielle est désactivée. Si de nombreux projets dépendants génèrent des fichiers .lib, la génération de l’application peut prendre un certain temps. Quand cette propriété a la valeur **Oui**, le système de projet lie les fichiers .obj des fichiers .lib produits par les projets dépendants, activant ainsi la liaison incrémentielle.

Pour plus d’informations sur l’accès à la page de propriétés **Général** de l’éditeur de liens, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Voir aussi

[Paramètres du projet VC++, Projets et solutions, boîte de dialogue Options](/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box)  
[Pages de propriétés](../ide/property-pages-visual-cpp.md)  