---
title: 'Pages de propriétés HLSL : Général'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
ms.openlocfilehash: 0fce8a3b2a43cf05024a028a9e3325a929922abb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825395"
---
# <a name="hlsl-property-pages-general"></a>Pages de propriétés HLSL : Général

Pour configurer les propriétés suivantes du compilateur HLSL (fxc.exe), utilisez sa page de propriétés **Général**. Pour plus d’informations sur l’accès à la **général** page de propriétés dans le dossier HLSL, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

## <a name="uielement-list"></a>Liste des éléments d’interface

- **Autres répertoires Include**

   Ajoute un ou plusieurs répertoires au chemin include. Utilisez des points-virgules pour séparer les répertoires.

Cette propriété correspond à l’argument de ligne de commande **/I[chemin]**.

- **Nom du point d’entrée**

   Spécifie le nom du point d’entrée pour le nuanceur. Par défaut, la valeur est **main**.

Cette propriété correspond à l’argument de ligne de commande **/E[nom]**.

- **Désactiver les optimisations**

   **Oui (/Od)** pour désactiver les optimisations ; sinon, **Non**. Par défaut, la valeur est **Oui (/Od)** pour les configurations **Debug** et **Non** pour les configurations **Release**.

L’argument de ligne de commande **/Od** du compilateur HLSL applique implicitement l’argument de ligne de commande **/Gfp**, mais la sortie peut ne pas être identique à la sortie qui est produite en passant explicitement les deux arguments de ligne de commande **/Od** et **/Gfp**.

- **Activer les informations de débogage**

   **Oui (/Zi)** pour activer les informations de débogage ; sinon, **Non**. Par défaut, la valeur est **Oui (/Zi)** pour les configurations **Debug** et **Non** pour les configurations **Release**.

- **Type de nuanceur**

   Spécifie le type de nuanceur. Les différents types de nuanceurs implémentent des parties différentes du pipeline graphique. Certains types de nuanceurs sont disponibles seulement dans les modèles de nuanceur les plus récents (qui sont spécifiés par la propriété **Modèle de nuanceur**) : par exemple, les nuanceurs de calcul ont été introduits dans le modèle de nuanceur 5.

   Cette propriété correspond à la partie **\[type]** de l’argument de ligne de commande **/T \[type]_\[modèle]** du compilateur HLSL. La propriété **Modèles de nuanceur** spécifie la partie **[modèle]** de l’argument.

- **Modèle de nuanceur**

   Spécifie le modèle de nuanceur. Les différents modèles de nuanceur ont des fonctionnalités différentes. En général, les modèles de nuanceur plus récents offrent des fonctionnalités étendues, mais ils nécessitent du matériel graphique plus moderne pour exécuter le code du nuanceur. Certains types de nuanceurs (qui sont spécifiés par la propriété **Type de nuanceur**) sont disponibles seulement dans les modèles de nuanceur les plus récents : par exemple, les nuanceurs de calcul ont été introduits dans le modèle de nuanceur 5.

   Cette propriété correspond à la partie **\[modèle]** de l’argument de ligne de commande **/T \[type]_\[modèle]** du compilateur HLSL. La propriété **Type de nuanceur** spécifie la partie **[type]** de l’argument.

- **Définitions de préprocesseur**

   Ajoute une ou plusieurs définitions de symbole de préprocesseur à appliquer au fichier de code source HLSL. Utilisez des points-virgules pour séparer les définitions de symbole.

   Cette propriété correspond à l’argument de ligne de commande **/D \[définitions]** du compilateur HLSL.

## <a name="see-also"></a>Voir aussi

[HLSL, page de propriétés](hlsl-property-pages.md)<br>
[HLSL, page de propriétés : Avancé](hlsl-property-pages-advanced.md)<br>
[HLSL, page de propriétés : Fichiers de sortie](hlsl-property-pages-output-files.md)
