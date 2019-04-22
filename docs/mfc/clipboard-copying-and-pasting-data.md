---
title: 'Presse-papiers : Copier et coller des données'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: cff9094315dc97e2040eb4dbad25d044c7c51a81
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58776100"
---
# <a name="clipboard-copying-and-pasting-data"></a>Presse-papiers : Copier et coller des données

Cette rubrique décrit les étapes nécessaires pour implémenter la copie et de collage à partir du Presse-papiers dans votre application OLE. Il est recommandé de lire le [objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md) rubriques avant de continuer.

Avant de pouvoir implémenter copie ou de collage, vous devez tout d’abord fournir des fonctions pour gérer les options de copier, couper et coller dans le menu Edition.

##  <a name="_core_copying_or_cutting_data"></a> Copie ou collage de données

#### <a name="to-copy-data-to-the-clipboard"></a>Pour copier des données dans le Presse-papiers

1. Déterminez si les données à copier sont des données natives ou est un élément incorporé ou lié.

   - Si les données sont incorporées ou liées, obtenir un pointeur vers le `COleClientItem` objet qui a été sélectionné.

   - Si les données sont natives et l’application est un serveur, créez un nouvel objet dérivé `COleServerItem` contenant les données sélectionnées. Sinon, créez un `COleDataSource` objet pour les données.

1. Appeler l’élément sélectionné `CopyToClipboard` fonction membre.

1. Si l’utilisateur a choisi une opération couper au lieu d’une opération de copie, supprimer les données sélectionnées à partir de votre application.

Pour voir un exemple de cette séquence, consultez le `OnEditCut` et `OnEditCopy` des exemples de fonctions dans les MFC OLE programmes [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md). Notez que ces exemples gèrent un pointeur vers les données sélectionnées, afin de l’étape 1 est déjà terminée.

##  <a name="_core_pasting_data"></a> Collage de données

Collage de données est plus complexe que la copie, car vous devez choisir le format à utiliser pour coller les données dans votre application.

#### <a name="to-paste-data-from-the-clipboard"></a>Pour coller des données à partir du Presse-papiers

1. Dans votre classe d’affichage, implémentez `OnEditPaste` pour gérer les utilisateurs en choisissant l’option Coller dans le menu Edition.

1. Dans le `OnEditPaste` de fonction, créez un `COleDataObject` objet et appelez ses `AttachClipboard` fonction membre à lier cet objet pour les données dans le Presse-papiers.

1. Appelez `COleDataObject::IsDataAvailable` pour vérifier si un format particulier est disponible.

   Vous pouvez également utiliser `COleDataObject::BeginEnumFormats` pour rechercher d’autres formats jusqu'à ce que vous trouviez un adapté à votre application.

1. Effectuer le collage du format.

Pour obtenir un exemple de comment cela fonctionne, consultez l’implémentation de la `OnEditPaste` fonctions membres dans les classes d’affichage définies dans les programmes exemples MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
>  Le principal avantage de la séparation de l’opération de collage dans sa propre fonction est que le même code de collage peut être utilisé lorsque les données sont déplacées dans votre application pendant une opération de glisser-déplacer. Comme dans OCLIENT et HIERSVR, votre `OnDrop` fonction peut également appeler `DoPasteItem`, réutilisant le code écrit pour l’implémentation des opérations de collage.

Pour gérer l’option Collage spécial dans le menu Edition, consultez la rubrique [boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)

- [Transferts de données uniformes et sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-ole.md)

- [Glisser-déplacer OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : À l’aide du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
