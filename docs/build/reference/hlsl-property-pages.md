---
description: En savoir plus sur les pages de propriétés du compilateur HLSL
title: Pages de propriétés HLSL
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: 3a374c36d87429fac9d9aee8dda2d1035da247c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199960"
---
# <a name="hlsl-compiler-property-pages"></a>Pages de propriétés du compilateur HLSL

Vous pouvez utiliser les pages de propriétés du compilateur HLSL (fxc.exe) pour configurer la façon dont les fichiers du nuanceur HLSL sont générés. Vous pouvez également spécifier des arguments de ligne de commande pour le compilateur HLSL à l’aide de la propriété **options supplémentaires** de la page de propriétés **ligne de commande** ; Cela comprend les arguments qui ne peuvent pas être configurés à l’aide d’autres propriétés des pages de propriétés HLSL. Pour plus d’informations sur le compilateur HLSL, consultez [Outil Compilateur d’effets](/windows/win32/direct3dtools/fxc)

## <a name="hlsl-general-property-page"></a>Page de propriétés général HLSL

### <a name="additional-include-directories"></a>Autres répertoires Include

Spécifie un ou plusieurs répertoires à ajouter au chemin include. Si vous ajoutez plusieurs répertoires, séparez-les par des points-virgules. (/I [chemin])

### <a name="entrypoint-name"></a>Nom du point d’entrée

Spécifie le nom du point d’entrée pour le nuanceur (/E [nom])

### <a name="disable-optimizations"></a>Désactiver les optimisations

**Oui (/Od)** pour désactiver les optimisations ; sinon, **Non**. Par défaut, la valeur est **Oui (/Od)** pour les configurations **Debug** et **Non** pour les configurations **Release**.

L’argument de ligne de commande **/Od** du compilateur HLSL applique implicitement l’argument de ligne de commande **/Gfp**, mais la sortie peut ne pas être identique à la sortie qui est produite en passant explicitement les deux arguments de ligne de commande **/Od** et **/Gfp**.

### <a name="enable-debugging-information"></a>Activer les informations de débogage

**Oui (/Zi)** pour activer les informations de débogage ; sinon, **Non**. Par défaut, la valeur est **Oui (/Zi)** pour les configurations **Debug** et **Non** pour les configurations **Release**.

### <a name="shader-type"></a>Type de nuanceur

Spécifie le type de nuanceur. Les différents types de nuanceurs implémentent des parties différentes du pipeline graphique. Certains types de nuanceurs sont disponibles seulement dans les modèles de nuanceur les plus récents (qui sont spécifiés par la propriété **Modèle de nuanceur**) : par exemple, les nuanceurs de calcul ont été introduits dans le modèle de nuanceur 5.

Cette propriété correspond à la partie **\[ type]** de l’argument de ligne de commande **/t \[ type] _ \[ Model]** au compilateur HLSL. La propriété **Modèles de nuanceur** spécifie la partie **[modèle]** de l’argument.

**Choices**

- **Effet**
- **Nuanceur de sommets**
- **Nuanceur de pixels**
- **Nuanceur de géométrie**
- **Nuanceur de coque**
- **Nuanceur de domaine**
- **Nuanceur de calcul**
- **Bibliothèque**
- **Générer un objet de signature racine**

### <a name="shader-model"></a>Modèle de nuanceur

Spécifie le modèle de nuanceur. Les différents modèles de nuanceur ont des fonctionnalités différentes. En général, les modèles de nuanceur plus récents offrent des fonctionnalités étendues, mais ils nécessitent du matériel graphique plus moderne pour exécuter le code du nuanceur. Certains types de nuanceurs (qui sont spécifiés par la propriété **Type de nuanceur**) sont disponibles seulement dans les modèles de nuanceur les plus récents : par exemple, les nuanceurs de calcul ont été introduits dans le modèle de nuanceur 5.

Cette propriété correspond à la partie **\[ Model]** de l’argument de ligne de commande **/t \[ type] _ \[ Model]** au compilateur HLSL. La propriété **Type de nuanceur** spécifie la partie **[type]** de l’argument.

### <a name="all-resources-bound"></a>Toutes les ressources liées

Le compilateur suppose que toutes les ressources qu’un nuanceur peut référencer sont liées et sont en bon état pendant la durée de l’exécution du nuanceur (/all_resources_bound). Disponible pour Shader Model 5.1 et les versions ultérieures.

### <a name="enable-unbounded-descriptor-tables"></a>Activer les tables de descripteurs non liées

Informez le compilateur qu’un nuanceur peut contenir une déclaration d’un tableau de ressources avec une plage illimitée (/enable_unbounded_descriptor_tables). Disponible pour Shader Model 5.1 et les versions ultérieures.

### <a name="set-root-signature"></a>Définir la signature racine

Attacher la signature racine au bytecode du nuanceur (/setrootsignature). Disponible pour Shader Model 5.0 et les versions ultérieures.

### <a name="preprocessor-definitions"></a>Définitions de préprocesseur

Ajoute une ou plusieurs définitions de symbole de préprocesseur à appliquer au fichier de code source HLSL. Utilisez des points-virgules pour séparer les définitions de symbole.

Cette propriété correspond à l’argument de ligne de commande **/D \[définitions]** du compilateur HLSL.

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>Compiler un effet de nuanceur de pixels personnalisé Direct2D

Compilez un effet personnalisé Direct2D qui contient des nuanceurs de pixels. N’utilisez pour un vertex ni ne calculez un effet personnalisé.

### <a name="multi-processor-compilation"></a>Compilation multiprocesseur

Exécutez plusieurs instances en même temps.

## <a name="advanced-property-page"></a>Page de propriétés avancé

### <a name="suppress-startup-banner"></a>Supprimer la bannière de démarrage

Supprime l’affichage de la bannière de démarrage et des messages d’information. /nologo

### <a name="treat-warnings-as-errors"></a>Considérer les avertissements comme des erreurs

Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il est conseillé d’utiliser /WX dans toutes les compilations, car la résolution de tous les avertissements permet de réduire les erreurs de code difficilement détectables.

## <a name="output-files-property-page"></a>Page de propriétés des fichiers de sortie

### <a name="header-variable-name"></a>Nom de la variable dans l’en-tête

Spécifie un nom pour le nom de la variable dans le fichier d’en-tête (/VN [name])

### <a name="header-file-name"></a>Nom du fichier d’en-tête

Spécifie un nom pour le fichier d’en-tête contenant le code objet. (/FH [name])

### <a name="object-file-name"></a>Nom de fichier objet

Spécifie un nom pour le fichier objet. (/FO [name])

### <a name="assembler-output"></a>Sortie de l’assembleur

Spécifie le contenu du fichier de sortie linguistique de l’assembly. (/FC,/FX)

**Choices**

- **Aucune liste** -aucune liste.
- **Listing assembleur uniquement** -fichier de code d’assembly
- Code **assembleur et** code d’assembly hexadécimal et fichier de liste hexadécimale

### <a name="assembler-output-file"></a>Fichier de sortie de l’assembleur

Spécifie le nom de fichier pour le fichier de liste de code assembleur

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les pages de propriétés de projet C++](property-pages-visual-cpp.md)<br>
[Pages de propriétés ligne de commande](command-line-property-pages.md)<br>
[Compilation des nuanceurs](/windows/win32/direct3dhlsl/dx-graphics-hlsl-part1)
