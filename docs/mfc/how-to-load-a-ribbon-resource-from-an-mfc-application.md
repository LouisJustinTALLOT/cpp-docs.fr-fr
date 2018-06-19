---
title: 'Comment : charger une ressource de ruban à partir d’une Application MFC | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b014e1725ae6c5043c051242a74e29338c3ef2d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344189"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Comment : charger une ressource du ruban à partir d'une application MFC
Pour utiliser la ressource de ruban dans votre application, modifiez l’application pour charger la ressource de ruban.  
  
### <a name="to-load-a-ribbon-resource"></a>Pour charger une ressource de ruban  
  
1.  Déclarez le `Ribbon Control` de l’objet dans la `CMainFrame` classe.  
  
 ```  
    CMFCRibbonBar m_wndRibbonBar;   
 ```  
  
2.  Dans `CMainFrame::OnCreate`, créer et initialiser le contrôle du ruban.  
  
 ```  
    if (!m_wndRibbonBar.Create (this))  
 {  
    return -1;  
 }  
 
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
 {  
    return -1;  
 }  
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur de ruban (MFC)](../mfc/ribbon-designer-mfc.md)

