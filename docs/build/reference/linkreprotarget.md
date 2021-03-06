---
title: /LINKREPROTARGET (Lier le nom du fichier de reproduction)
description: Option de l’éditeur de liens ou de l’outil bibliothèque pour définir un nom de fichier cible pour une reproduction de lien.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: d629c4c2665239d03f38569677fa579b6c8d37e0
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712680"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET (Lier le nom du fichier de reproduction)

Indique à l’éditeur de liens ou à l’outil de bibliothèque de générer une reproduction de lien uniquement lorsque la cible porte le nom de fichier spécifié.

## <a name="syntax"></a>Syntaxe

> **/LINKREPROTARGET :** _nom de fichier_

### <a name="arguments"></a>Arguments

**/LINKREPROTARGET :** _nom de fichier_\
Nom du fichier cible sur lequel effectuer le filtrage. Une reproduction de lien est générée uniquement lorsque le fichier nommé est la cible de sortie. Les noms de fichiers qui contiennent des espaces doivent être placés entre guillemets doubles. Le nom de fichier doit inclure le nom de base et l’extension, mais pas le chemin d’accès.

## <a name="remarks"></a>Notes

L’option **/LINKREPROTARGET** est utilisée pour spécifier un nom de fichier cible pour lequel générer une *reproduction de lien* . Une reproduction de lien est un ensemble d’artefacts de build qui permettent à Microsoft de reproduire un problème qui se produit au moment de la liaison ou pendant les opérations de la bibliothèque. L’éditeur de liens ou l’outil de bibliothèque produit une reproduction de lien lorsque vous spécifiez l’option [/LINKREPRO](linkrepro.md) , ou lorsque vous définissez la variable d’environnement `link_repro` dans votre environnement de génération en ligne de commande.

L’option **/LINKREPROTARGET** est utile dans les builds complexes qui appellent l’éditeur de liens ou l’outil de bibliothèque plusieurs fois. Elle vous permet de spécifier une cible spécifique pour la reproduction de lien, par exemple, *problem. dll*. Elle vous permet de générer la reproduction de lien uniquement lorsque l’outil produit un fichier spécifique.

Pour plus d’informations sur la façon et le moment de créer une reproduction de lien, consultez la section relative aux reproductions de [liens](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) dans Guide pratique [pour signaler un problème avec l’ensemble d’outils Microsoft C++ ](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Les options **/LINKREPRO** et [/out](out-output-file-name.md) doivent être définies pour que l’option **/LINKREPROTARGET** ait un effet.

**/LINKREPROTARGET** est disponible à partir de Visual Studio 2019 version 16,1.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés ligne de **commande** .

1. Entrez l’option **/LINKREPROTARGET :** _nom de fichier_ dans la zone **options supplémentaires** . Choisissez **OK** pour appliquer le changement.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

\ de référence de l' [éditeur de liens MSVC](linking.md)
[Options de l’éditeur de liens MSVC](linker-options.md)\
[/LINKREPRO](linkrepro.md)
