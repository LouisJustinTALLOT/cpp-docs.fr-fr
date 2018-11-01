---
title: Gestionnaires définis par l'utilisateur
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.handlers
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: 4d2102668b7cc964e6fe3bffdcc6931a2961a737
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562251"
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

[Tables des messages](../../mfc/reference/message-maps-mfc.md)<br/>
[Gestionnaires de messages WM_](../../mfc/reference/handlers-for-wm-messages.md)

