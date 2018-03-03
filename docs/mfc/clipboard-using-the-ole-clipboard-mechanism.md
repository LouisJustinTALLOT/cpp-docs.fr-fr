---
title: "Presse-papiers : Utilisation du mécanisme de Presse-papiers OLE | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4996c6559ad20141fb84ed37e87fd1551e89a77b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Presse-papiers : utilisation du mécanisme de Presse-papiers OLE
OLE utilise des formats standard et certains formats spécifiques à OLE pour transférer des données via le Presse-papiers.  
  
 Lorsque vous découpez ou copiez des données à partir d'une application, les données sont stockées dans le Presse-papiers pour être utilisées ultérieurement dans les opérations de collage. Ces données sont disponibles dans une variété de formats. Lorsqu'un utilisateur choisit de coller des données à partir du Presse-papiers, l'application peut choisir le format à utiliser. L'application doit être écrite pour choisir le format qui offre le plus d'informations, à moins que l'utilisateur demande spécifiquement un certain format, en utilisant le Collage spécial. Avant de continuer, il pouvez que vous souhaitez lire le [des objets de données et Sources de données (OLE)](../mfc/data-objects-and-data-sources-ole.md) rubriques. Elles décrivent les aspects fondamentaux de la façon dont les transferts de données fonctionnent, et leur implémentation dans vos applications.  
  
 Windows définit plusieurs formats standard qui peuvent être utilisés pour transférer des données dans le Presse-papiers. Cela inclut les métafichiers, le texte, les images bitmap, entre autres. OLE définit également plusieurs formats spécifiques OLE. Pour les applications qui nécessitent plus de détail que spécifié par ces formats standard, il est judicieux d'enregistrer leurs propres formats personnalisés de presse-papiers. Utilisez la fonction API Win32 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) pour ce faire.  
  
 Par exemple, Microsoft Excel enregistre un format personnalisé pour les feuilles de calcul. Ce format contient davantage d'informations qu'une image bitmap, par exemple. Lorsque ces données sont collées dans une application qui prend en charge le format feuille de calcul, toutes les formules et valeurs de la feuille de calcul sont conservées et peuvent être mises à jour si nécessaire. Microsoft Excel met également des données formatées dans le Presse-papiers afin qu'elles puissent être collées comme des éléments OLE. Tout conteneur de document OLE peut également coller ces informations comme éléments incorporés. Ces éléments incorporés peuvent être modifiés à l'aide de Microsoft Excel. Le Presse-papiers contient également une bitmap simple de l'image de la plage sélectionnée dans la feuille de calcul. Ceci peut aussi être collé dans des conteneurs de document OLE ou dans des éditeurs de bitmap, comme Paint. Dans le cas d'une bitmap, toutefois, il n'existe aucune méthode pour manipuler les données sous la forme d'une feuille de calcul.  
  
 Pour récupérer le maximum d'informations du Presse-papiers, les applications doivent vérifier ces formats personnalisés avant de copier les données du Presse-papiers.  
  
 Par exemple, pour activer la commande Couper, vous pouvez entrer un gestionnaire similaire à ce qui suit :  
  
 [!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Copier et coller des données](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Ajout d’autres formats](../mfc/clipboard-adding-other-formats.md)  
  
-   [Utilisation du Presse-papiers Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [Transfert de données uniforme et les sources de données et les objets de données OLE](../mfc/data-objects-and-data-sources-ole.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Presse-papiers](../mfc/clipboard.md)

