---
title: Gestionnaires définis par l’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.handlers
dev_langs:
- C++
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8fdc8c70f7ef9bdd04bf40f408c4e014b3e3faa3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33373244"
---
# <a name="user-defined-handlers"></a>Gestionnaires définis par l'utilisateur
Les entrées de mappage suivantes correspondent aux prototypes de fonction.  
  
|Entrée de mappage|Prototype de fonction|  
|---------------|------------------------|  
|ON_MESSAGE ( \<message >, \<memberFxn >)|afx_msg LRESULT memberFxn (WPARAM, LPARAM) ;|  
|ON_REGISTERED_MESSAGE ( \<nMessageVariable >, \<memberFxn >)|afx_msg LRESULT memberFxn (WPARAM, LPARAM) ;|  
|ON_THREAD_MESSAGE ( \<message >, \<memberFxn >)|memberFxn de void afx_msg (WPARAM, LPARAM) ;|  
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable >, \<memberFxn >)|memberFxn de void afx_msg (WPARAM, LPARAM) ;|  
  
## <a name="see-also"></a>Voir aussi  
 [Tables des messages](../../mfc/reference/message-maps-mfc.md)   
 [Gestionnaires de messages WM_](../../mfc/reference/handlers-for-wm-messages.md)

