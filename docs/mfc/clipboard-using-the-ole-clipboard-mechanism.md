---
description: 'En savoir plus sur : presse-papiers : utilisation du mécanisme de presse-papiers OLE'
title: 'Presse-papiers : utilisation du mécanisme de Presse-papiers OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: f7005bd3e99ebb658b6aa38952a6689d4a9ba30c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338436"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Presse-papiers : utilisation du mécanisme de Presse-papiers OLE

OLE utilise des formats standard et certains formats spécifiques à OLE pour transférer des données via le Presse-papiers.

Lorsque vous découpez ou copiez des données à partir d'une application, les données sont stockées dans le Presse-papiers pour être utilisées ultérieurement dans les opérations de collage. Ces données sont disponibles dans une variété de formats. Lorsqu'un utilisateur choisit de coller des données à partir du Presse-papiers, l'application peut choisir le format à utiliser. L'application doit être écrite pour choisir le format qui offre le plus d'informations, à moins que l'utilisateur demande spécifiquement un certain format, en utilisant le Collage spécial. Avant de continuer, vous souhaiterez peut-être lire les rubriques [objets de données et sources de données (OLE)](data-objects-and-data-sources-ole.md) . Elles décrivent les aspects fondamentaux de la façon dont les transferts de données fonctionnent, et leur implémentation dans vos applications.

Windows définit plusieurs formats standard qui peuvent être utilisés pour transférer des données dans le Presse-papiers. Cela inclut les métafichiers, le texte, les images bitmap, entre autres. OLE définit également plusieurs formats spécifiques OLE. Pour les applications qui nécessitent plus de détail que spécifié par ces formats standard, il est judicieux d'enregistrer leurs propres formats personnalisés de presse-papiers. Pour ce faire, utilisez la fonction API Win32 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

Par exemple, Microsoft Excel enregistre un format personnalisé pour les feuilles de calcul. Ce format contient davantage d'informations qu'une image bitmap, par exemple. Lorsque ces données sont collées dans une application qui prend en charge le format feuille de calcul, toutes les formules et valeurs de la feuille de calcul sont conservées et peuvent être mises à jour si nécessaire. Microsoft Excel met également des données formatées dans le Presse-papiers afin qu'elles puissent être collées comme des éléments OLE. Tout conteneur de document OLE peut également coller ces informations comme éléments incorporés. Ces éléments incorporés peuvent être modifiés à l'aide de Microsoft Excel. Le Presse-papiers contient également une bitmap simple de l'image de la plage sélectionnée dans la feuille de calcul. Ceci peut aussi être collé dans des conteneurs de document OLE ou dans des éditeurs de bitmap, comme Paint. Dans le cas d'une bitmap, toutefois, il n'existe aucune méthode pour manipuler les données sous la forme d'une feuille de calcul.

Pour récupérer le maximum d'informations du Presse-papiers, les applications doivent vérifier ces formats personnalisés avant de copier les données du Presse-papiers.

Par exemple, pour activer la commande Couper, vous pouvez entrer un gestionnaire similaire à ce qui suit :

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Copie et collage de données](clipboard-copying-and-pasting-data.md)

- [Ajout d’autres formats](clipboard-adding-other-formats.md)

- [Utilisation du presse-papiers Windows](clipboard-using-the-windows-clipboard.md)

- [OLE](ole-background.md)

- [Objets de données et sources de données OLE et transfert de données uniforme](data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>Voir aussi

[Presse-papiers](clipboard.md)
