---
title: "L’utilisation du contrôle RichEdit 1.0 avec MFC | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- RichEdit 1.0 control
- rich edit controls, RichEdit 1.0
ms.assetid: 5a9060dd-44d8-4ef3-956e-16152f7e23d2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3d6c5393b006602084a50d18c8cfe76d59d2d6ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-richedit-10-control-with-mfc"></a>Utilisation du contrôle RichEdit 1.0 avec MFC
Pour utiliser un contrôle RichEdit, vous devez d’abord appeler [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) pour charger le contrôle RichEdit 2.0 (RICHED20. (DLL), ou appelez [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) pour charger l’ancien contrôle RichEdit 1.0 (Riched32). (DLL).  
  
 Vous pouvez utiliser actuel [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) classe avec l’ancien contrôle RichEdit 1.0, mais **CRichEditCtrl** est conçu uniquement pour prendre en charge le contrôle RichEdit 2.0. Étant donné que RichEdit 1.0 et RichEdit 2.0 sont très similaires, la plupart des méthodes fonctionneront ; Notez, toutefois, il existe des différences entre les contrôles 1.0 et 2.0, et certaines méthodes peuvent fonctionner de manière incorrecte ou ne fonctionne pas du tout.  
  
## <a name="requirements"></a>Configuration requise  
 MFC  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’éditeur de boîte de dialogue](../windows/troubleshooting-the-dialog-editor.md)   
 [Éditeur de boîtes de dialogue](../windows/dialog-editor.md)

