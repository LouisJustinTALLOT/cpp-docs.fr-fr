---
title: 'Étape de génération personnalisée, page de propriétés : général'
description: Cet article décrit les propriétés disponibles dans la page étape de génération personnalisée de la boîte de dialogue pages de propriétés.
ms.date: 10/27/2020
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: 53f2deef931821981b3301f44ba37660975fb811
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907582"
---
# <a name="custom-build-step-property-page-general"></a>Étape de génération personnalisée, page de propriétés : général

Pour chaque combinaison de configuration de projet et de plateforme cible dans votre projet, vous pouvez spécifier une étape personnalisée à exécuter lorsque le projet est généré.

Pour obtenir la version Linux de cette page, consultez [Étape de build personnalisée, propriétés (Linux C++)](../../linux/prop-pages/custom-build-step-linux.md).

## <a name="general-page"></a>Page Général

- **Ligne de commande**

   Commande à exécuter par l'étape de génération personnalisée.

- **Description**

   Message qui s'affiche lors de l'exécution de l'étape de génération personnalisée.

- **Sorties**

   Fichier de sortie généré lors de l'étape de génération personnalisée. Ce paramètre est requis afin que les générations incrémentielles fonctionnent correctement.

- **Dépendances supplémentaires**

   Liste délimitée par les points-virgules de tous les fichiers d'entrée supplémentaires à utiliser pour l'étape de génération personnalisée.

- **Exécution après et Exécution avant**

   Ces options définissent le moment de l'exécution de l'étape de génération personnalisée dans le processus de génération, par rapport aux cibles répertoriées. Les cibles les plus couramment répertoriées sont `BuildGenerateSources` , `BuildCompile` et `BuildLink` , car elles représentent les principales étapes du processus de génération. Les autres cibles souvent répertoriées sont `Midl` , `CLCompile` et `Link` .

- **Considérer la sortie en tant que contenu**

   Cette option est significative uniquement pour les applications plateforme Windows universelle ou Windows Phone, qui incluent tous les fichiers de contenu du *`.appx`* Package.

### <a name="to-specify-a-custom-build-step"></a>Pour spécifier une étape de génération personnalisée

1. Dans la barre de menus, choisissez Propriétés du **projet**  >  **Properties** . Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans la boîte de dialogue **pages de propriétés** , accédez à la page **Propriétés de configuration**  >  étape générale de **génération personnalisée**  >  **General** .

1. Modifier les paramètres du site.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les pages de propriétés de projet C++](property-pages-visual-cpp.md)
