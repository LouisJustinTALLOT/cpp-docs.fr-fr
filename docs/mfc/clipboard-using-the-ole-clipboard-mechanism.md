---
title: 'Presse-papiers : À l’aide du mécanisme de Presse-papiers OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: d8ef93b306c0968adf2c23c841c792d2f7af5de3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327039"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Presse-papiers : À l’aide du mécanisme de Presse-papiers OLE

OLE utilise des formats standard et certains formats spécifiques à OLE pour transférer des données via le Presse-papiers.

Lorsque vous découpez ou copiez des données à partir d'une application, les données sont stockées dans le Presse-papiers pour être utilisées ultérieurement dans les opérations de collage. Ces données sont disponibles dans une variété de formats. Lorsqu'un utilisateur choisit de coller des données à partir du Presse-papiers, l'application peut choisir le format à utiliser. L'application doit être écrite pour choisir le format qui offre le plus d'informations, à moins que l'utilisateur demande spécifiquement un certain format, en utilisant le Collage spécial. Avant de continuer, il pouvez que vous souhaitez lire le [objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md) rubriques. Elles décrivent les aspects fondamentaux de la façon dont les transferts de données fonctionnent, et leur implémentation dans vos applications.

Windows définit plusieurs formats standard qui peuvent être utilisés pour transférer des données dans le Presse-papiers. Cela inclut les métafichiers, le texte, les images bitmap, entre autres. OLE définit également plusieurs formats spécifiques OLE. Pour les applications qui nécessitent plus de détail que spécifié par ces formats standard, il est judicieux d'enregistrer leurs propres formats personnalisés de presse-papiers. Utilisez la fonction API Win32 [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) pour ce faire.

Par exemple, Microsoft Excel enregistre un format personnalisé pour les feuilles de calcul. Ce format contient davantage d'informations qu'une image bitmap, par exemple. Lorsque ces données sont collées dans une application qui prend en charge le format feuille de calcul, toutes les formules et valeurs de la feuille de calcul sont conservées et peuvent être mises à jour si nécessaire. Microsoft Excel met également des données formatées dans le Presse-papiers afin qu'elles puissent être collées comme des éléments OLE. Tout conteneur de document OLE peut également coller ces informations comme éléments incorporés. Ces éléments incorporés peuvent être modifiés à l'aide de Microsoft Excel. Le Presse-papiers contient également une bitmap simple de l'image de la plage sélectionnée dans la feuille de calcul. Ceci peut aussi être collé dans des conteneurs de document OLE ou dans des éditeurs de bitmap, comme Paint. Dans le cas d'une bitmap, toutefois, il n'existe aucune méthode pour manipuler les données sous la forme d'une feuille de calcul.

Pour récupérer le maximum d'informations du Presse-papiers, les applications doivent vérifier ces formats personnalisés avant de copier les données du Presse-papiers.

Par exemple, pour activer la commande Couper, vous pouvez entrer un gestionnaire similaire à ce qui suit :

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)

- [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)

- [Utilisation du Presse-papiers Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [OLE](../mfc/ole-background.md)

- [Transferts de données uniformes et sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers](../mfc/clipboard.md)
