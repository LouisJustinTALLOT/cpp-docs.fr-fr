---
title: 'Presse-papiers : copier-coller des données'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374568"
---
# <a name="clipboard-copying-and-pasting-data"></a>Presse-papiers : copier-coller des données

Ce sujet décrit le travail minimum nécessaire pour implémenter la copie et le coller à partir du Clipboard dans votre application OLE. Il est recommandé de lire les sujets [des objets et des sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md) avant de procéder.

Avant de pouvoir implémenter la copie ou le coller, vous devez d’abord fournir des fonctions pour gérer les options Copier, Couper et Coller sur le menu Modifier.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Copier ou couper des données

#### <a name="to-copy-data-to-the-clipboard"></a>Pour copier les données du Clipboard

1. Déterminez si les données à copier sont des données natives ou s’il s’agit d’un élément intégré ou lié.

   - Si les données sont intégrées ou `COleClientItem` liées, obtenez un pointeur sur l’objet qui a été sélectionné.

   - Si les données sont natives et que l’application `COleServerItem` est un serveur, créez un nouvel objet dérivé de la contenant des données sélectionnées. Sinon, créez `COleDataSource` un objet pour les données.

1. Appelez la fonction `CopyToClipboard` de membre de l’élément sélectionné.

1. Si l’utilisateur a choisi une opération Cut au lieu d’une opération Copy, supprimez les données sélectionnées de votre application.

Pour voir un exemple de `OnEditCut` cette `OnEditCopy` séquence, voir les et les fonctions dans les programmes d’échantillons MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md). Notez que ces échantillons conservent un pointeur sur les données actuellement sélectionnées, de sorte que l’étape 1 est déjà terminée.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Données de coller

Coller des données est plus compliqué que de les copier parce que vous devez choisir le format à utiliser pour coller les données dans votre application.

#### <a name="to-paste-data-from-the-clipboard"></a>Pour coller les données du Clipboard

1. Dans votre classe `OnEditPaste` de vue, implémentez pour gérer les utilisateurs choisissant l’option Pâte du menu Edit.

1. Dans `OnEditPaste` la fonction, `COleDataObject` créez un `AttachClipboard` objet et appelez sa fonction de membre pour lier cet objet aux données du Clipboard.

1. Appelez `COleDataObject::IsDataAvailable` pour vérifier si un format particulier est disponible.

   Alternativement, vous `COleDataObject::BeginEnumFormats` pouvez utiliser pour rechercher d’autres formats jusqu’à ce que vous trouviez un plus adapté à votre application.

1. Effectuez la pâte du format.

Par exemple, voir la mise en `OnEditPaste` œuvre des fonctions des membres dans les classes de vue définies dans les programmes d’échantillons [OCLIENT](../overview/visual-cpp-samples.md) et [HIERSVR](../overview/visual-cpp-samples.md)de MFC .

> [!TIP]
> Le principal avantage de séparer l’opération de pâte dans sa propre fonction est que le même code de pâte peut être utilisé lorsque les données sont supprimées dans votre application lors d’une opération de drag-and-drop. Comme dans OCLIENT et HIERSVR, `OnDrop` `DoPasteItem`votre fonction peut également appeler , réutiliser le code écrit pour implémenter les opérations de pâte.

Pour gérer l’option Pâte Spéciale sur le menu Edit, voir le sujet [Dialog Boxes in OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)

- [Objets de données et sources de données OLE et transfert de données uniforme](../mfc/data-objects-and-data-sources-ole.md)

- [Glisser-déposer OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers : utilisation du mécanisme de Presse-papiers OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
