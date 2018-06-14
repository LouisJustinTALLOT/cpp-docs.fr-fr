---
title: 'Pages de propriétés HLSL : Général | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs:
- C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77cc9a44076999633fd17b049cbcfad75f65eb7e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340136"
---
# <a name="hlsl-property-pages-general"></a>Pages de propriétés HLSL : Général
Pour configurer les propriétés suivantes du compilateur HLSL (fxc.exe), utilisez sa page de propriétés **Général**. Pour plus d’informations sur l’accès à la page de propriétés **Général** dans le dossier HLSL, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Autres répertoires Include**  
 Ajoute un ou plusieurs répertoires au chemin include. Utilisez des points-virgules pour séparer les répertoires.  
  
 Cette propriété correspond à l’argument de ligne de commande **/I[chemin]**.  
  
 **Nom du point d’entrée**  
 Spécifie le nom du point d’entrée pour le nuanceur. Par défaut, la valeur est **main**.  
  
 Cette propriété correspond à l’argument de ligne de commande **/E[nom]**.  
  
 **Désactiver les optimisations**  
 **Oui (/Od)** pour désactiver les optimisations ; sinon, **Non**. Par défaut, la valeur est **Oui (/Od)** pour les configurations **Debug** et **Non** pour les configurations **Release**.  
  
 L’argument de ligne de commande **/Od** du compilateur HLSL applique implicitement l’argument de ligne de commande **/Gfp**, mais la sortie peut ne pas être identique à la sortie qui est produite en passant explicitement les deux arguments de ligne de commande **/Od** et **/Gfp**.  
  
 **Activer les informations de débogage**  
 **Oui (/Zi)** pour activer les informations de débogage ; sinon, **Non**. Par défaut, la valeur est **Oui (/Zi)** pour les configurations **Debug** et **Non** pour les configurations **Release**.  
  
 **Type de nuanceur**  
 Spécifie le type de nuanceur. Les différents types de nuanceurs implémentent des parties différentes du pipeline graphique. Certains types de nuanceurs sont disponibles seulement dans les modèles de nuanceur les plus récents (qui sont spécifiés par la propriété **Modèle de nuanceur**) : par exemple, les nuanceurs de calcul ont été introduits dans le modèle de nuanceur 5.  
  
 Cette propriété correspond à la partie **[type]** de l’argument de ligne de commande **/T [type]_[modèle]** du compilateur HLSL. La propriété **Modèles de nuanceur** spécifie la partie **[modèle]** de l’argument.  
  
 **Modèle de nuanceur**  
 Spécifie le modèle de nuanceur. Les différents modèles de nuanceur ont des fonctionnalités différentes. En général, les modèles de nuanceur plus récents offrent des fonctionnalités étendues, mais ils nécessitent du matériel graphique plus moderne pour exécuter le code du nuanceur. Certains types de nuanceurs (qui sont spécifiés par la propriété **Type de nuanceur**) sont disponibles seulement dans les modèles de nuanceur les plus récents : par exemple, les nuanceurs de calcul ont été introduits dans le modèle de nuanceur 5.  
  
 Cette propriété correspond à la partie **[modèle]** de l’argument de ligne de commande **/T [type]_[modèle]** du compilateur HLSL. La propriété **Type de nuanceur** spécifie la partie **[type]** de l’argument.  
  
 **Définitions de préprocesseur**  
 Ajoute une ou plusieurs définitions de symbole de préprocesseur à appliquer au fichier de code source HLSL. Utilisez des points-virgules pour séparer les définitions de symbole.  
  
 Cette propriété correspond à la partie **/D [définitions]** de l’argument de ligne de commande du compilateur HLSL.  
  
## <a name="see-also"></a>Voir aussi  
 [HLSL, page de propriétés](../ide/hlsl-property-pages.md)   
 [HLSL, page de propriétés : Avancé](../ide/hlsl-property-pages-advanced.md)   
 [HLSL, page de propriétés : fichiers de sortie](../ide/hlsl-property-pages-output-files.md)