---
title: 'Presse-papiers : Ajout d’autres Formats'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 16e949973ff621b1e4e36475d95763ac47b4a00d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280216"
---
# <a name="clipboard-adding-other-formats"></a>Presse-papiers : Ajout d’autres Formats

Cette rubrique explique comment développer la liste des formats pris en charge, en particulier pour la prise en charge OLE. La rubrique [Presse-papiers : Copie et collage de données](../mfc/clipboard-copying-and-pasting-data.md) décrit l’implémentation minimale nécessaire pour prendre en charge la copie et collage depuis le Presse-papiers. Si c’est tout ce vous implémentez, les seuls formats placés dans le Presse-papiers sont **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**et éventuellement **CF_LINKSOURCE**. La plupart des applications nécessitent d’autres formats dans le Presse-papiers à ces trois.

##  <a name="_core_registering_custom_formats"></a> Enregistrement de Formats personnalisés

Pour créer vos propres formats personnalisés, suivez la même procédure que vous utiliseriez lors de l’inscription de n’importe quel format de Presse-papiers personnalisé : passez le nom du format à la **RegisterClipboardFormat** de fonction et utiliser sa valeur de retour comme ID de format.

##  <a name="_core_placing_formats_on_the_clipboard"></a> Ajout de Formats dans le Presse-papiers

Pour ajouter d’autres formats à ceux placés dans le Presse-papiers, vous devez substituer la `OnGetClipboardData` fonction dans la classe dérivée à partir de le `COleClientItem` ou `COleServerItem` (selon que les données à copier sont natives). Dans cette fonction, vous devez utiliser la procédure suivante.

#### <a name="to-place-formats-on-the-clipboard"></a>Pour placer des formats dans le Presse-papiers

1. Créez un objet `COleDataSource`.

1. Passez cette source de données à une fonction qui ajoute vos formats de données natifs à la liste des formats pris en charge en appelant `COleDataSource::CacheGlobalData`.

1. Ajoutez des formats standard en appelant `COleDataSource::CacheGlobalData` pour chaque format standard que vous souhaitez prendre en charge.

Cette technique est utilisée dans le programme d’exemple OLE MFC [HIERSVR](../visual-cpp-samples.md) (examiner le `OnGetClipboardData` fonction membre de la **CServerItem** classe). La seule différence dans cet exemple est que l’étape trois n’est pas implémentée, car HIERSVR prend en charge aucun autre format standard.

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Transferts de données uniformes et sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-ole.md)

- [Glisser-déplacer OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
