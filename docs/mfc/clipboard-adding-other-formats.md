---
title: "Presse-papiers : ajout d'autres formats"
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374605"
---
# <a name="clipboard-adding-other-formats"></a>Presse-papiers : ajout d'autres formats

Ce sujet explique comment élargir la liste des formats pris en charge, en particulier pour le soutien OLE. Le sujet [Clipboard: Copying and Pasting Data](../mfc/clipboard-copying-and-pasting-data.md) décrit la mise en œuvre minimale nécessaire pour prendre en charge la copie et le coller du Clipboard. Si c’est tout ce que vous implémentez, les seuls formats placés sur le Clipboard sont **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**, et peut-être **CF_LINKSOURCE**. La plupart des applications auront besoin de plus de formats sur le Clipboard que ces trois.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Enregistrement des formats personnalisés

Pour créer vos propres formats personnalisés, suivez la même procédure que vous utiliseriez lors de l’enregistrement de n’importe quel format Clipboard personnalisé : transmettez le nom du format à la fonction **RegisterClipboardFormat** et utilisez sa valeur de retour comme ID format.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Placer des formats sur le Clipboard

Pour ajouter plus de formats à ceux placés `OnGetClipboardData` sur le Clipboard, `COleClientItem` vous `COleServerItem` devez remplacer la fonction dans la classe que vous avez dérivée de l’une ou l’autre ou (selon que les données à copier sont indigènes). Dans cette fonction, vous devez utiliser la procédure suivante.

#### <a name="to-place-formats-on-the-clipboard"></a>Placer des formats sur le Clipboard

1. Créez un objet `COleDataSource`.

1. Transmettez cette source de données à une fonction qui ajoute vos formats de données natifs à la liste des formats pris en charge en appelant `COleDataSource::CacheGlobalData`.

1. Ajoutez des formats `COleDataSource::CacheGlobalData` standard en appelant pour chaque format standard que vous souhaitez prendre en charge.

Cette technique est utilisée dans le programme d’échantillons `OnGetClipboardData` DE LOL MFC [HIERSVR](../overview/visual-cpp-samples.md) (examiner la fonction membre de la classe **CServerItem).** La seule différence dans cet échantillon est que l’étape trois n’est pas implémentée parce qu’HIERSVR ne prend en charge aucun autre format standard.

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Objets de données et sources de données OLE et transfert de données uniforme](../mfc/data-objects-and-data-sources-ole.md)

- [Glisser-déposer OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : utilisation du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
