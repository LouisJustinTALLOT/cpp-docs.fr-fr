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
ms.openlocfilehash: 52089364a6be423c69a7031cd0d99e1924de1444
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626061"
---
# <a name="clipboard-adding-other-formats"></a>Presse-papiers : ajout d'autres formats

Cette rubrique explique comment développer la liste des formats pris en charge, en particulier pour la prise en charge OLE. La rubrique [presse-papiers : copier-coller des données](clipboard-copying-and-pasting-data.md) décrit l’implémentation minimale nécessaire pour prendre en charge la copie et le collage à partir du presse-papiers. S’il s’agit de tout ce que vous implémentez, les seuls formats placés dans le presse-papiers sont **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**et éventuellement **CF_LINKSOURCE**. La plupart des applications ont besoin d’un plus grand nombre de formats dans le presse-papiers que ces trois.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Inscription des formats personnalisés

Pour créer vos propres formats personnalisés, suivez la même procédure que celle utilisée lors de l’inscription d’un format de presse-papiers personnalisé : transmettez le nom du format à la fonction **RegisterClipboardFormat** et utilisez sa valeur de retour comme ID de format.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Placement de formats dans le presse-papiers

Pour ajouter d’autres formats à ceux placés dans le presse-papiers, vous devez substituer la `OnGetClipboardData` fonction dans la classe que vous avez dérivée de `COleClientItem` ou `COleServerItem` (selon que les données à copier sont natives ou non). Dans cette fonction, vous devez utiliser la procédure suivante.

#### <a name="to-place-formats-on-the-clipboard"></a>Pour placer les formats dans le presse-papiers

1. Créez un objet `COleDataSource`.

1. Transmettez cette source de données à une fonction qui ajoute vos formats de données natifs à la liste des formats pris en charge en appelant `COleDataSource::CacheGlobalData` .

1. Ajoutez des formats standard en appelant `COleDataSource::CacheGlobalData` pour chaque format standard que vous souhaitez prendre en charge.

Cette technique est utilisée dans l’exemple de programme OLE MFC [HIERSVR](../overview/visual-cpp-samples.md) (examinez la `OnGetClipboardData` fonction membre de la classe **CServerItem** ). La seule différence dans cet exemple est que l’étape 3 n’est pas implémentée, car HIERSVR ne prend pas en charge d’autres formats standard.

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Objets de données et sources de données OLE et transfert de données uniforme](data-objects-and-data-sources-ole.md)

- [Glisser-déposer OLE](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : utilisation du mécanisme de Presse-papiers OLE](clipboard-using-the-ole-clipboard-mechanism.md)
