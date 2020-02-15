---
title: /WHOLEARCHIVE (inclure tous les fichiers objets de la bibliothèque)
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 95685c9c0dfde45c42449bbcad67228a0e21b36a
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257531"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (inclure tous les fichiers objets de la bibliothèque)

Force l’éditeur de liens à inclure tous les fichiers objets de la bibliothèque statique dans l’exécutable lié.

## <a name="syntax"></a>Syntaxe

> **/WHOLEARCHIVE**\
> **/WHOLEARCHIVE :** _bibliothèque_

### <a name="arguments"></a>Arguments

*bibliothèque*\
Nom de chemin d’accès facultatif à une bibliothèque statique. L’éditeur de liens comprend chaque fichier objet de cette bibliothèque.

## <a name="remarks"></a>Notes

L’option/WHOLEARCHIVE force l’éditeur de liens à inclure chaque fichier objet d’une bibliothèque statique spécifiée, ou si aucune bibliothèque n’est spécifiée, à partir de toutes les bibliothèques statiques spécifiées dans la commande LINK. Pour spécifier l’option/WHOLEARCHIVE pour plusieurs bibliothèques, vous pouvez utiliser plusieurs commutateurs/WHOLEARCHIVE sur la ligne de commande de l’éditeur de liens. Par défaut, l’éditeur de liens comprend les fichiers objets de la sortie liée uniquement s’ils exportent des symboles référencés par d’autres fichiers objets dans l’exécutable. L’option/WHOLEARCHIVE permet à l’éditeur de liens de traiter tous les fichiers objets archivés dans une bibliothèque statique comme s’ils étaient spécifiés individuellement sur la ligne de commande de l’éditeur de liens.

L’option/WHOLEARCHIVE peut être utilisée pour réexporter tous les symboles d’une bibliothèque statique. Cela vous permet de vous assurer que l’ensemble du code, des ressources et des métadonnées de votre bibliothèque sont inclus lorsque vous créez un composant à partir de plusieurs bibliothèques statiques. Si vous voyez un avertissement LNK4264 quand vous créez une bibliothèque statique qui contient des composants de Windows Runtime pour l’exportation, utilisez l’option/WHOLEARCHIVE lors de la liaison de cette bibliothèque à un autre composant ou une autre application.

L’option/WHOLEARCHIVE a été introduite dans Visual Studio 2015 Update 2.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **ligne de commande** sous **Propriétés de configuration**, éditeur de **liens**.

1. Ajoutez l’option/WHOLEARCHIVE à la zone de texte **options supplémentaires** .

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
