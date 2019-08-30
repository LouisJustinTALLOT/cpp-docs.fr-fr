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
ms.openlocfilehash: 916b6615d80000d601c909f771a1ec8f1b947927
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177338"
---
# <a name="resources-property-page"></a>Ressources, page de propriétés

Pour les programmes de bureau Windows natifs, la génération appelle le [compilateur de ressources (RC. exe)](/windows/win32/menurc/resource-compiler) pour ajouter des images, des tables de chaînes et des fichiers *. res* au fichier binaire. Les propriétés exposées dans cette page de propriétés sont passées au compilateur de ressources, pas au C++ compilateur ou à l’éditeur de liens. Pour plus d’informations sur les propriétés répertoriées ici et la façon dont elles sont mappées à des options de ligne de commande RC, consultez [utilisation de RC (ligne de commande RC)](/windows/win32/menurc/using-rc-the-rc-command-line-). Pour plus d’informations sur la façon d’accéder aux pages de propriétés des **ressources** , consultez [définir C++ les propriétés de compilation et de compilation dans Visual Studio](../working-with-project-properties.md). Pour accéder par programmation à ces propriétés, consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Les propriétés des ressources .NET C++dans les applications/CLI sont exposées dans la [page de propriétés ressources managées](managed-resources-property-page.md).

## <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Spécifie une ou plusieurs définitions pour le compilateur de ressources. (/d [macro])

## <a name="undefine-preprocessor-definitions"></a>Annuler la définition de définitions de préprocesseur

Annule la définition d’un symbole. /u.

## <a name="culture"></a>culture

Répertorie la culture (par exemple, anglais (États-Unis) ou italien) utilisée dans les ressources. (/l [num])

## <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter au chemin d’accès include; Utilisez un point-virgule de délimitation si plusieurs. (/I [chemin])

## <a name="ignore-standard-include-paths"></a>Ignorer les chemins d’accès Include standard

Empêche le compilateur de ressources de rechercher les fichiers include dans les répertoires spécifiés dans les variables d’environnement INCLUDe. /PATH

## <a name="show-progress"></a>Afficher la progression

Envoie des messages d’avancement à la fenêtre sortie. /f

## <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprimer l’affichage de la bannière de démarrage et du message d’information (/nologo)

## <a name="resource-file-name"></a>Nom du fichier de ressources

Spécifie le nom du fichier de ressources (/FO [fichier])

## <a name="null-terminate-strings"></a>Chaînes de fin null 

Ajoutez la valeur null à toutes les chaînes des tables de chaînes. /n

## <a name="see-also"></a>Voir aussi

[C++Référence de la page de propriétés du projet](property-pages-visual-cpp.md)