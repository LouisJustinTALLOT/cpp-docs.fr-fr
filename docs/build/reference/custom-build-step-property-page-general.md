---
title: 'Étape de génération personnalisée, page de propriétés : Général'
ms.date: 11/04/2016
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
ms.openlocfilehash: 329923140cf5a8f05e5c032ddb9e25c0ea45ec2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273077"
---
# <a name="custom-build-step-property-page-general"></a>Étape de génération personnalisée, page de propriétés : Général

Pour chaque combinaison de configuration de projet et de plateforme cible dans votre projet, vous pouvez spécifier une étape personnalisée à effectuer lors de la génération du projet.

Pour obtenir la version Linux de cette page, consultez [Étape de build personnalisée, propriétés (Linux C++)](../../linux/prop-pages/custom-build-step-linux.md).

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Ligne de commande**

   Commande à exécuter par l'étape de génération personnalisée.

- **Description**

   Message qui s'affiche lors de l'exécution de l'étape de génération personnalisée.

- **Sorties**

   Fichier de sortie généré lors de l'étape de génération personnalisée. Ce paramètre est requis afin que les générations incrémentielles fonctionnent correctement.

- **Dépendances supplémentaires**

   Liste délimitée par les points-virgules de tous les fichiers d'entrée supplémentaires à utiliser pour l'étape de génération personnalisée.

- **Exécution après et Exécution avant**

   Ces options définissent le moment de l'exécution de l'étape de génération personnalisée dans le processus de génération, par rapport aux cibles répertoriées. Les cibles le plus souvent répertoriées sont BuildGenerateSources, BuildCompile, et BuildLink, car elles constituent des étapes majeures dans le processus de génération. Les cibles souvent répertoriées sont Midl, CLCompile, et Link.

- **Considérer la sortie en tant que contenu**

   Cette option est utile uniquement dans la plateforme Windows universelle ou les applications Windows Phone, qui contiennent tous les fichiers de contenu du package .appx.

### <a name="to-specify-a-custom-build-step"></a>Pour spécifier une étape de génération personnalisée

1. Dans la barre de menus, choisissez **Projet**, **Propriétés**. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Dans la boîte de dialogue **Pages de propriétés**, naviguez jusqu’à la page **Propriétés de configuration**, **Étape de build personnalisée**, **Général**.

1. Modifier les paramètres du site.

## <a name="see-also"></a>Voir aussi

[Référence de page de propriété de projet C++](property-pages-visual-cpp.md)
