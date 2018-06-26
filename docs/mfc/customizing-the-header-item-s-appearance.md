---
title: Personnalisation de l’élément d’en-tête&#39;s apparence | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e09f8bc0b61e22435ee348968f117940b57132e3
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930873"
---
# <a name="customizing-the-header-item39s-appearance"></a>Personnalisation de l’élément d’en-tête&#39;s apparence
En définissant le *dwStyle* paramètre lorsque vous créez un contrôle header ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), vous pouvez définir l’apparence et comportement de l’en-tête d’éléments ou de l’en-tête de contrôle lui-même.  
  
 Voici les styles que vous pouvez définir et leur objectif :  
  
-   Pour rendre un élément d’en-tête ressembler à un bouton de commande, utilisez le **HDS_BUTTONS** style.  
  
     Utilisez ce type si vous souhaitez exécuter des actions en réponse aux clics de souris sur un élément d’en-tête, telles que le tri des données à une colonne particulière, comme c’est le cas dans Microsoft Outlook.  
  
-   Pour donner les éléments d’en-tête une apparence « suivi » lorsque le curseur de souris passe dessus, utilisez le **HDS_HOTTRACK** style.  
  
     Suivi affiche un contour 3D lorsque le pointeur passe sur un élément dans un plat sinon barre.  
  
-   Pour indiquer que le contrôle header doit être masqué, utilisez le **HDS_HIDDEN** style.  
  
     Le **HDS_HIDDEN** style indique que le contrôle header est destiné à être utilisé comme un conteneur de données et pas un contrôle visuel. Ce style ne masque pas automatiquement le contrôle mais, au lieu de cela, affecte le comportement de `CHeaderCtrl::Layout`. La valeur retournée dans le *cy* membre de la `WINDOWPOS` structure sera égal à zéro qui indique que le contrôle ne doit pas être visible par l’utilisateur.  
  
 Pour plus d’informations sur ces propriétés, consultez [éléments](http://msdn.microsoft.com/library/windows/desktop/bb775238) dans le Kit de développement logiciel Windows. Pour plus d’informations sur l’ajout d’éléments à un contrôle header, consultez [Ajout d’éléments au contrôle Header](../mfc/adding-items-to-the-header-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

