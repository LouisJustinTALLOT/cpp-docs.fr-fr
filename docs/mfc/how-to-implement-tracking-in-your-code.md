---
title: 'Comment : implémenter le suivi dans votre Code | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CRectTracker class [MFC], implementing trackers
ms.assetid: baaeca2c-5114-485f-bf58-8807db1bc973
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc21369dd8d241bd00da2a0a8005c977094c3abf
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932092"
---
# <a name="how-to-implement-tracking-in-your-code"></a>Comment : implémenter le suivi dans votre code
Pour suivre un élément OLE, vous devez gérer certains événements associés à l'élément, tel que cliquer sur l'élément ou mettre à jour la vue du document. Dans tous les cas, il suffit de déclarer une variable temporaire [CRectTracker](../mfc/reference/crecttracker-class.md) et de manipuler l’élément au moyen de cet objet.  
  
 Lorsqu'un utilisateur sélectionne un élément ou insère un objet avec une commande de menu, vous devez initialiser le mécanisme de suivi avec les styles appropriés pour représenter l'état de l'élément OLE. Le tableau suivant présente les conventions utilisées par l'exemple OCLIENT. Pour plus d'informations sur ces styles, consultez `CRectTracker`.  
  
### <a name="container-styles-and-states-of-the-ole-item"></a>Styles de conteneur et états de l'élément OLE  
  
|Style d'affichage|État de l'élément OLE|  
|---------------------|-----------------------|  
|Bordure en pointillés|L'élément est lié|  
|Bordure pleine|L'élément est incorporé dans le document|  
|Poignées de redimensionnement|L'élément est actuellement sélectionné|  
|Bordure hachurée|L'élément est actuellement actif en place|  
|Le modèle de hachurage recouvre l'élément|Le serveur de l'élément est ouvert|  
  
 Vous pouvez traiter cette initialisation facilement à l'aide d'une procédure qui vérifie l'état de l'élément OLE et qui définit les styles appropriés. Le `SetupTracker` fonction se trouve dans l’exemple OCLIENT illustre l’initialisation de suivi. Les paramètres de cette fonction sont l’adresse du dispositif de suivi, *pTracker*; un pointeur vers l’élément client qui est liée à la mise hors tension, *pItem*; et un pointeur vers un rectangle, *pTrueRect* . Pour obtenir un exemple plus complet de cette fonction, consultez l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md).  
  
 Le **SetupTracker** exemple de code présente une seule fonction ; les lignes de la fonction sont mélangées à savoir plus sur les fonctionnalités de la fonction :  
  
 [!code-cpp[NVC_MFCOClient#1](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_1.cpp)]  
  
 Le dispositif de suivi est initialisé en définissant la taille minimale et en effaçant le style du dispositif de suivi.  
  
 [!code-cpp[NVC_MFCOClient#2](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_2.cpp)]  
  
 Les lignes suivantes permettent de voir si l'élément est sélectionné et si l'élément est lié au document ou incorporé dans celui-ci. Des poignées de redimensionnement placées à l'intérieur de la bordure sont ajoutées au style, ce qui indique que l'élément est sélectionné. Si l'élément est lié à votre document, le style de bordure en pointillés est utilisé. Une bordure pleine est utilisée si l'élément est incorporé.  
  
 [!code-cpp[NVC_MFCOClient#3](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_3.cpp)]  
  
 Le code suivant recouvre l’élément avec un modèle hachuré si l’élément est ouvert.  
  
 [!code-cpp[NVC_MFCOClient#4](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_4.cpp)]  
  
 Vous pouvez ensuite appeler cette fonction lorsque le mécanisme de suivi doit être affiché. Par exemple, appeler cette fonction depuis la fonction `OnDraw` de votre classe d'affichage. Cela met à jour l'apparence du dispositif de suivi lorsque la vue est redessinée. Pour obtenir un exemple complet, consultez la `CMainView::OnDraw` fonction de l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md).  
  
 Dans votre application, les événements qui requièrent un code de suivi, tel que le redimensionnement, le déplacement ou la détection d'accès, se produisent. Ces actions indiquent généralement qu'une tentative a lieu pour saisir ou déplacer l'élément. Dans ce cas, vous devez déterminer ce qui a été saisi : une poignée de redimensionnement ou une partie de la bordure entre les poignées de redimensionnement. Le gestionnaire de messages `OnLButtonDown` est un bon endroit pour tester la position de la souris par rapport à l'élément. Effectuez un appel à `CRectTracker::HitTest`. Si le test retourne une valeur autre que `CRectTracker::hitOutside`, l’élément est redimensionné ou déplacé. Par conséquent, vous devez effectuer un appel à la fonction membre `Track`. Consultez le `CMainView::OnLButtonDown` (fonction) se trouve dans l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md) pour obtenir un exemple complet.  
  
 La classe `CRectTracker` fournit différentes formes de curseur utilisées pour indiquer si un déplacement, un redimensionnement ou un glissement a lieu. Pour gérer l'événement, activez la case à cocher pour déterminer si l'élément actuellement sous la souris est sélectionné. Si tel est le cas, effectuez un appel à `CRectTracker::SetCursor` ou appelez le gestionnaire par défaut. L’exemple suivant est tiré de l’exemple OLE MFC [OCLIENT](../visual-cpp-samples.md):  
  
 [!code-cpp[NVC_MFCOClient#5](../mfc/codesnippet/cpp/how-to-implement-tracking-in-your-code_5.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Dispositifs de suivi : implémentation de dispositifs de suivi dans votre application OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)

