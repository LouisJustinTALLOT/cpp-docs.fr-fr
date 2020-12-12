---
description: En savoir plus sur les gestionnaires de User-Defined
title: Gestionnaires définis par l'utilisateur
ms.date: 11/04/2016
helpviewer_keywords:
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_MESSAGE macro [MFC]
- user-defined handlers [MFC]
ms.assetid: 99478294-bef0-4ba7-a369-25a6abdcdb62
ms.openlocfilehash: 8a3b7389d7388fb54ae39d3b1805594b64556652
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218522"
---
# <a name="user-defined-handlers"></a>Gestionnaires définis par l'utilisateur

Les entrées de mappage suivantes correspondent aux prototypes de fonction.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|ON_MESSAGE ( \<message> , \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_MESSAGE ( \<nMessageVariable> , \<memberFxn> )|afx_msg LRESULT memberFxn (WPARAM, LPARAM);|
|ON_THREAD_MESSAGE ( \<message> , \<memberFxn> )|afx_msg void memberFxn (WPARAM, LPARAM);|
|ON_REGISTERED_THREAD_MESSAGE ( \<nMessageVariable> , \<memberFxn> )|afx_msg void memberFxn (WPARAM, LPARAM);|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)<br/>
[Gestionnaires pour les messages de WM_](../../mfc/reference/handlers-for-wm-messages.md)
