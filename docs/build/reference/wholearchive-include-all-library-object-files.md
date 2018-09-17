---
title: -WHOLEARCHIVE (inclure tous les fichiers d’objet de bibliothèque) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3a59ed53227e0c9bf598f96b1bb72247a3341b0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722245"
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (inclure tous les fichiers d’objet de bibliothèque)

Force l’éditeur de liens à inclure tous les fichiers d’objet dans la bibliothèque statique dans le fichier exécutable lié.

## <a name="syntax"></a>Syntaxe

> / WHOLEARCHIVE [ :*bibliothèque*]

## <a name="remarks"></a>Notes

L’option /WHOLEARCHIVE force l’éditeur de liens à inclure tous les fichiers à partir de l’objet une bibliothèque statique spécifiée, ou si aucune bibliothèque n’est spécifié, à partir de toutes les bibliothèques statiques spécifiés pour le lien de commande. Pour spécifier l’option /WHOLEARCHIVE pour plusieurs bibliothèques, vous pouvez utiliser plusieurs /WHOLEARCHIVE basculer sur la ligne de commande de l’éditeur de liens. Par défaut, l’éditeur de liens inclut les fichiers de l’objet dans la sortie liée uniquement si elles exportent les symboles référencés par d’autres fichiers de l’objet dans le fichier exécutable. L’option /WHOLEARCHIVE permet à l’éditeur de liens de traiter tous les fichiers objet archivées dans une bibliothèque statique comme s’ils ont été spécifiés individuellement sur la ligne de commande de l’éditeur de liens.

L’option /WHOLEARCHIVE peut être utilisée pour exporter de nouveau tous les symboles à partir d’une bibliothèque statique. Cela vous permet de vous assurer que toutes les votre code de bibliothèque, les ressources et les métadonnées sont incluses lorsque vous créez un composant à partir de plusieurs bibliothèques statiques. Si vous voyez l’avertissement LNK4264 lorsque vous créez une bibliothèque statique qui contient les composants Windows Runtime pour l’exportation, utilisez l’option /WHOLEARCHIVE lors de la liaison de cette bibliothèque dans une autre application ou composant.

L’option /WHOLEARCHIVE a été introduite dans Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **ligne de commande** page de propriétés **propriétés de Configuration**, **l’éditeur de liens**.

1. Ajoutez l’option /WHOLEARCHIVE à la **des Options supplémentaires** zone de texte.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)