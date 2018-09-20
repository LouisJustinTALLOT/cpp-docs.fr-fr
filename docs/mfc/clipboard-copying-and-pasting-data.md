---
title: 'Presse-papiers : Copier et coller des données | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15a03708f96f881206aa683b31c26c3c5192f8cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389055"
---
# <a name="clipboard-copying-and-pasting-data"></a>Presse-papiers : copier-coller des données

Cette rubrique décrit les étapes nécessaires pour implémenter la copie et de collage à partir du Presse-papiers dans votre application OLE. Il est recommandé de lire le [objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md) rubriques avant de continuer.

Avant de pouvoir implémenter copie ou de collage, vous devez tout d’abord fournir des fonctions pour gérer les options de copier, couper et coller dans le menu Edition.

##  <a name="_core_copying_or_cutting_data"></a> Copie ou collage de données

#### <a name="to-copy-data-to-the-clipboard"></a>Pour copier des données dans le Presse-papiers

1. Déterminez si les données à copier sont des données natives ou est un élément incorporé ou lié.

   - Si les données sont incorporées ou liées, obtenir un pointeur vers le `COleClientItem` objet qui a été sélectionné.

   - Si les données sont natives et l’application est un serveur, créez un nouvel objet dérivé `COleServerItem` contenant les données sélectionnées. Sinon, créez un `COleDataSource` objet pour les données.

1. Appeler l’élément sélectionné `CopyToClipboard` fonction membre.

1. Si l’utilisateur a choisi une opération couper au lieu d’une opération de copie, supprimer les données sélectionnées à partir de votre application.

Pour voir un exemple de cette séquence, consultez le `OnEditCut` et `OnEditCopy` des exemples de fonctions dans les MFC OLE programmes [OCLIENT](../visual-cpp-samples.md) et [HIERSVR](../visual-cpp-samples.md). Notez que ces exemples gèrent un pointeur vers les données sélectionnées, afin de l’étape 1 est déjà terminée.

##  <a name="_core_pasting_data"></a> Collage de données

Collage de données est plus complexe que la copie, car vous devez choisir le format à utiliser pour coller les données dans votre application.

#### <a name="to-paste-data-from-the-clipboard"></a>Pour coller des données à partir du Presse-papiers

1. Dans votre classe d’affichage, implémentez `OnEditPaste` pour gérer les utilisateurs en choisissant l’option Coller dans le menu Edition.

1. Dans le `OnEditPaste` de fonction, créez un `COleDataObject` objet et appelez ses `AttachClipboard` fonction membre à lier cet objet pour les données dans le Presse-papiers.

1. Appelez `COleDataObject::IsDataAvailable` pour vérifier si un format particulier est disponible.

     Vous pouvez également utiliser `COleDataObject::BeginEnumFormats` pour rechercher d’autres formats jusqu'à ce que vous trouviez un adapté à votre application.

1. Effectuer le collage du format.

Pour obtenir un exemple de comment cela fonctionne, consultez l’implémentation de la `OnEditPaste` fonctions membres dans les classes d’affichage définies dans les programmes exemples MFC OLE [OCLIENT](../visual-cpp-samples.md) et [HIERSVR](../visual-cpp-samples.md).

> [!TIP]
>  Le principal avantage de la séparation de l’opération de collage dans sa propre fonction est que le même code de collage peut être utilisé lorsque les données sont déplacées dans votre application pendant une opération de glisser-déplacer. Comme dans OCLIENT et HIERSVR, votre `OnDrop` fonction peut également appeler `DoPasteItem`, réutilisant le code écrit pour l’implémentation des opérations de collage.

Pour gérer l’option Collage spécial dans le menu Edition, consultez la rubrique [boîtes de dialogue dans OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)

- [Transferts de données uniformes et sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-ole.md)

- [Glisser-déplacer OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : utilisation du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

