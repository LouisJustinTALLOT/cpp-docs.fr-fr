---
title: /LINKREPRO (Lier le nom du répertoire de reproduction)
description: Option de l’éditeur de liens ou de l’outil bibliothèque pour définir le répertoire d’une reproduction de lien.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686851"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO (Lier le nom du répertoire de reproduction)

Indique à l’éditeur de liens ou à l’outil de bibliothèque de générer une reproduction de lien dans un répertoire spécifié.

## <a name="syntax"></a>Syntaxe

> **/LINKREPRO :** _nom du répertoire_

### <a name="arguments"></a>Arguments

**/LINKREPRO :** _nom de répertoire_\
Répertoire spécifié par l’utilisateur dans lequel stocker la reproduction du lien. Les noms de répertoires qui incluent des espaces doivent être placés entre guillemets doubles.

## <a name="remarks"></a>Notes

L’option **/LINKREPRO** permet de créer une *reproduction de lien*. Il s’agit d’un ensemble d’artefacts de build qui permettent à Microsoft de reproduire un problème qui se produit au moment de la liaison ou pendant les opérations de la bibliothèque. Elle est utile pour des problèmes tels qu’un blocage de backend impliquant la génération de code durant l’édition de liens (LTCG), une erreur de l’éditeur de liens LNK1000 ou un incident de l’éditeur de liens. L’outil produit une reproduction de lien lorsque vous spécifiez l’option de l’éditeur de liens **/LINKREPRO** , ou lorsque vous définissez la variable d’environnement `link_repro` dans votre environnement de génération en ligne de commande. Pour plus d’informations, consultez la section relative aux reproductions de [liens](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) dans Guide pratique [pour C++ signaler un problème avec l’ensemble d’outils Microsoft](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

L’option de l’éditeur de liens **/LINKREPRO** et la variable d’environnement `link_repro` nécessitent que vous spécifiiez un répertoire de sortie pour la reproduction de lien. Sur la ligne de commande ou dans l’IDE, spécifiez le répertoire à l’aide de l’option **/LINKREPRO :** _Directory-Name_ . Le _nom de répertoire_ que vous spécifiez peut être un chemin d’accès absolu ou relatif, mais le répertoire doit exister. L’option de ligne de commande remplace toute valeur de répertoire définie dans la variable d’environnement `link_repro`.

Pour plus d’informations sur la façon de limiter la génération de la reproduction des liens à un nom de fichier cible spécifique, consultez l’option [/LINKREPROTARGET](linkreprotarget.md) . Cette option peut être utilisée pour spécifier une cible spécifique pour laquelle générer une reproduction de lien. Elle est utile dans les builds complexes qui appellent l’éditeur de liens ou l’outil de bibliothèque plusieurs fois.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés ligne de **commande** .

1. Entrez l’option **/LINKREPRO :** _nom-répertoire_ dans la zone **options supplémentaires** . La valeur _de nom de répertoire_ que vous spécifiez doit exister. Choisissez **OK** pour appliquer le changement.

Une fois que vous avez généré la reproduction de lien, ouvrez à nouveau cette page de propriétés pour supprimer l’option **/LINKREPRO** de vos builds.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

\ de référence de l' [éditeur de liens MSVC](linking.md)
[Options de l’éditeur de liens MSVC](linker-options.md)\
[/LINKREPROTARGET](linkreprotarget.md)
