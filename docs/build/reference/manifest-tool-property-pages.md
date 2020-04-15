---
title: Pages de propriétés de l'outil Manifeste
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: e1d0f1ac889cb915216ceb70d48e36efe4ad21bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336295"
---
# <a name="manifest-tool-property-pages"></a>Pages de propriétés de l'outil Manifeste

Utilisez ces pages pour spécifier les options générales pour [Mt.exe](/windows/win32/sbscs/mt-exe). Ces pages se trouvent dans **le cadre de Project** > **Properties** > **Configuration Properties** > **Manifest Tool**.

## <a name="general-property-page"></a>Page de propriétés Général

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

   **Oui (/nologo)** spécifie que les données de copyright standard de Microsoft n’apparaîtront pas au démarrage de l’outil Manifeste. Utilisez cette option pour supprimer les sorties dont vous ne voulez pas dans les fichiers journaux, quand vous exécutez mt.exe dans le cadre d’un processus de génération ou à partir d’un environnement de génération.

### <a name="verbose-output"></a>Sortie Verbose

   **Oui (/verbose)** spécifie que des informations de build supplémentaires seront affichées pendant la génération du manifeste.

### <a name="assembly-identity"></a>Identité d’assembly

Utilise l’option /identité pour spécifier une chaîne d’identité, qui comprend les attributs pour [ \<l’assemblageIdentity> Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application). Une chaîne d’identité commence `name` par la valeur de l’attribut, et est suivie par des paires*de valeur* *d’attribut.* =  Les attributs dans une chaîne d’identité sont délimités par une virgule.

Il s’agit d’un exemple de chaîne d’identité:`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Page de propriété d’entrée et de sortie

### <a name="additional-manifest-files"></a>Fichiers manifeste supplémentaires

Utilise l’option **/manifest** pour spécifier les chemins complets des fichiers manifeste supplémentaires que l’outil Manifeste traitera ou fusionnera. Les chemins complets sont délimités par un point-virgule. (-manifeste [manifeste1] [manifeste2] ...)

### <a name="input-resource-manifests"></a>Manifestes de ressource d’entrée

Utilise l’option **/inputresource** pour spécifier le chemin complet d’une ressource de type RT_MANIFEST, à entrer dans l’outil Manifeste. Le chemin peut être suivi de l’ID de ressource spécifié. Par exemple :

`dll_with_manifest.dll;#1`

### <a name="embed-manifest"></a>Incorporer le manifeste

- **Oui** spécifie que le système de projet incorporera le fichier manifeste d’application dans l’assembly.

- **Non** spécifie que le système de projet créera le fichier manifeste d’application en tant que fichier autonome.

### <a name="output-manifest-file"></a>Fichier manifeste de sortie

Spécifie le nom du fichier manifeste de sortie. Cette propriété est facultative quand un seul fichier manifeste est traité par l’outil Manifeste. (-out:[file];[resource ID])

### <a name="manifest-resource-file"></a>Fichier de ressources du manifeste

Spécifie le fichier de ressources de sortie utilisé pour incorporer le manifeste dans la sortie du projet.

### <a name="generate-catalog-files"></a>Génération de fichiers catalogue

Utilise l’option **/makecdfs** pour spécifier que l’outil Manifeste générera des fichiers de définition de catalogue (fichiers .cdf), qui sont utilisés pour faire des catalogues. (/makecdfs)

### <a name="generate-manifest-from-managedassembly"></a>Génération du manifeste à partir de ManagedAssembly

Génère un manifeste à partir d’un assembly managé. (-managedassemblyname:\[fichier))

### <a name="suppress-dependency-element"></a>Suppression des éléments de dépendance

Utilisé avec-managedassembly. supprime la génération d’éléments de dépendance dans le manifeste final. (-nodependance)

### <a name="generate-category-tags"></a>Génération des indicateurs de catégorie

Utilisé avec-managedassembly. -catégorie provoque la génération des étiquettes de catégorie. (-catégorie)

### <a name="dpi-awareness"></a>Sensibilisation à l’IPI

Spécifie si l’application prend en charge DPI. Par défaut, le paramètre a la valeur **Oui** pour les projets MFC et **Non** pour les autres projets parce que seuls les projets MFC présentent une prise en charge DPI intégrée. Vous pouvez remplacer le paramètre par **Oui** si vous ajoutez du code pour gérer différents paramètres DPI. Votre application peut apparaître floue ou petite si vous la définissez comme prenant en charge DPI quand ce n’est pas le cas.

**Choix**

- **Aucun**
- **Haute DPI Aware**
- **Par Moniteur Haute DPI Conscient**

## <a name="isolated-com-property-page"></a>Page de propriété ISOLÉE com

Pour plus d’informations sur le COM isolé, voir [les applications isolées](/windows/win32/SbsCs/isolated-applications) et [comment : construire des applications isolées pour consommer des composants COM](../how-to-build-isolated-applications-to-consume-com-components.md).

### <a name="type-library-file"></a>Fichier bibliothèque de types

Spécifie la bibliothèque type à utiliser pour le support manifeste REGfree COM. (-tlb:[fichier])

### <a name="registrar-script-file"></a>Fichier de script d’inscription

Spécifie le fichier de script du registraire à utiliser pour le support manifeste regfree COM. (-rgs:[fichier])

### <a name="component-file-name"></a>Nom de fichier du composant

Spécifie le nom de fichier du composant qui est construit à partir de la .tlb ou .rgs spécifié. (-dll:[fichier])

### <a name="replacements-file"></a>Fichier de remplacement

Spécifie le fichier qui contient des valeurs pour les chaînes remplaçables dans le fichier RGS. (remplacements:[fichier])

## <a name="advanced-property-page"></a>Page de propriété avancée

### <a name="update-file-hashes"></a>Mettre à jour les fichiers à hacher

Calcule le hachage des fichiers spécifiés dans les éléments de fichier et met à jour l’attribut de hachage avec cette valeur. (hashupdate:[chemin])

### <a name="update-file-hashes-search-path"></a>Chemin de recherche de mise à jour des fichiers à hacher

Spécifie le chemin de recherche à utiliser lors de la mise à jour des hachages de fichiers.

### <a name="additional-options"></a>Options supplémentaires

Options supplémentaires

## <a name="see-also"></a>Voir aussi

[Référence de page de propriété du projet CMD](property-pages-visual-cpp.md)
