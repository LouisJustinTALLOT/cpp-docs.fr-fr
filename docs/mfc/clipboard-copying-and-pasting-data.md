---
description: 'En savoir plus sur : presse-papiers : copier et coller des données'
title: 'Presse-papiers : copier-coller des données'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: fdc102cf7a92bc78df83419269bb5de828dc9d19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251230"
---
# <a name="clipboard-copying-and-pasting-data"></a>Presse-papiers : copier-coller des données

Cette rubrique décrit le travail minimum nécessaire pour implémenter la copie vers et le collage à partir du presse-papiers dans votre application OLE. Avant de continuer, il est recommandé de lire les rubriques relatives aux [objets de données et sources de données (OLE)](data-objects-and-data-sources-ole.md) .

Avant de pouvoir implémenter la copie ou le collage, vous devez d’abord fournir des fonctions pour gérer les options copier, couper et coller du menu Edition.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a> Copie ou découpe de données

#### <a name="to-copy-data-to-the-clipboard"></a>Pour copier des données dans le presse-papiers

1. Déterminez si les données à copier sont des données natives ou s’il s’agit d’un élément incorporé ou lié.

   - Si les données sont incorporées ou liées, obtenez un pointeur vers l' `COleClientItem` objet qui a été sélectionné.

   - Si les données sont natives et que l’application est un serveur, créez un nouvel objet dérivé de `COleServerItem` contenant les données sélectionnées. Dans le cas contraire, créez un `COleDataSource` objet pour les données.

1. Appelez la fonction membre de l’élément sélectionné `CopyToClipboard` .

1. Si l’utilisateur a choisi une opération couper au lieu d’une opération de copie, supprimez les données sélectionnées de votre application.

Pour voir un exemple de cette séquence, consultez les `OnEditCut` `OnEditCopy` fonctions et dans les exemples de programmes OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md). Notez que ces exemples maintiennent un pointeur vers les données actuellement sélectionnées. l’étape 1 est donc déjà terminée.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a> Coller des données

Le collage de données est plus complexe que la copie, car vous devez choisir le format à utiliser pour coller les données dans votre application.

#### <a name="to-paste-data-from-the-clipboard"></a>Pour coller des données à partir du presse-papiers

1. Dans votre classe d’affichage, implémentez `OnEditPaste` pour gérer les utilisateurs qui choisissent l’option coller dans le menu Edition.

1. Dans la `OnEditPaste` fonction, créez un `COleDataObject` objet et appelez sa `AttachClipboard` fonction membre pour lier cet objet aux données du presse-papiers.

1. Appelez `COleDataObject::IsDataAvailable` pour vérifier si un format particulier est disponible.

   Vous pouvez également utiliser `COleDataObject::BeginEnumFormats` pour rechercher d’autres formats jusqu’à ce que vous en trouviez un le plus adapté à votre application.

1. Effectuez le collage du format.

Pour obtenir un exemple de fonctionnement, consultez l’implémentation des `OnEditPaste` fonctions membres dans les classes d’affichage définies dans les exemples de programmes OLE MFC [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
> Le principal avantage de la séparation de l’opération de collage dans sa propre fonction est que le même code de collage peut être utilisé lorsque les données sont supprimées dans votre application pendant une opération de glisser-déplacer. Comme dans OCLIENT et HIERSVR, votre `OnDrop` fonction peut également appeler `DoPasteItem` , réutiliser le code écrit pour implémenter les opérations de collage.

Pour gérer l’option Collage spécial dans le menu Edition, consultez la rubrique [boîtes de dialogue dans OLE](dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Ajout d’autres formats](clipboard-adding-other-formats.md)

- [Objets de données et sources de données OLE et transfert de données uniforme](data-objects-and-data-sources-ole.md)

- [Glisser-déposer OLE](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : utilisation du mécanisme de presse-papiers OLE](clipboard-using-the-ole-clipboard-mechanism.md)
