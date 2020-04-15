---
title: Ressources
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336077"
---
# <a name="resources-property-page"></a>Page de propriété des ressources

Pour les programmes de bureau Windows natifs, la version invoque le [compilateur de ressources (rc.exe)](/windows/win32/menurc/resource-compiler) pour ajouter des images, des tables de chaîne et des fichiers *.res* au binaire. Les propriétés exposées dans cette page de propriété sont transmises au compilateur de ressources, et non au compilateur CMD ou au lien. Pour plus d’informations sur les propriétés énumérées ici et comment elles cartographient les options de ligne de commande RC, voir [Using RC (The RC Command Line)](/windows/win32/menurc/using-rc-the-rc-command-line-). Pour plus d’informations sur la façon d’accéder aux pages de propriété **Des Ressources,** consultez [le compilateur Set CMD et construisez des propriétés dans Visual Studio](../working-with-project-properties.md). Pour accéder par programmation à ces propriétés, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Les propriétés pour les ressources .NET dans les applications CMD/CLI sont exposées dans la [page propriété des ressources gérées](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Spécifie une ou plusieurs définitions pour le compilateur de ressources. (/d[macro])

## <a name="undefine-preprocessor-definitions"></a>Annuler la définition de définitions de préprocesseur

Indéfinis un symbole. (/u)

## <a name="culture"></a>Culture

Répertorie la culture (comme l’anglais ou l’italien des États-Unis) utilisée dans les ressources. (/l [num])

## <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter au chemin inclus; utiliser semi-colon delimiter si plus d’un. (/I[chemin])

## <a name="ignore-standard-include-paths"></a>Ignorer la norme Inclure les chemins

Empêche le compilateur de ressources de rechercher des fichiers dans les répertoires spécifiés dans les variables de l’environnement INCLUDE. (/X)

## <a name="show-progress"></a>Afficher la progression

Envoyez des messages de progression à la fenêtre de sortie. (/v)

## <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprimer l’affichage de la bannière de démarrage et le message d’information (/nologo)

## <a name="resource-file-name"></a>Nom du fichier de ressources

Précise le nom du fichier des ressources (/fo[file])

## <a name="null-terminate-strings"></a>Null Terminate Strings

Annexe nulle à toutes les cordes dans les tables à cordes. (/n)

## <a name="see-also"></a>Voir aussi

[Référence de page de propriété du projet CMD](property-pages-visual-cpp.md)
