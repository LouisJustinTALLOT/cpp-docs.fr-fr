---
description: 'En savoir plus sur : gestionnaires de zone de liste'
title: Gestionnaires de zones de liste
ms.date: 11/04/2016
f1_keywords:
- ON_LBN_DBLCLK
- ON_LBN_ERRSPACE
- ON_LBN_SETFOCUS
- ON_LBN_SELCHANGE
- ON_LBN_KILLFOCUS
helpviewer_keywords:
- list boxes [MFC], list box handlers
- ON_LBN_KILLFOCUS
- ON_LBN_ERRSPACE
- ON_LBN_SELCHANGE
- ON_LBN_SETFOCUS
- ON_LBN_DBLCLK
ms.assetid: e4e54412-2167-436a-883b-5dcad01820b8
ms.openlocfilehash: 190833fed725009729a5895f3b302da4c897fb51
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219419"
---
# <a name="list-box-handlers"></a>Gestionnaires de zones de liste

Les entrées de mappage suivantes ont le prototype de fonction correspondant.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|ON_LBN_DBLCLK ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_LBN_ERRSPACE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_LBN_KILLFOCUS ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_LBN_SELCHANGE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_LBN_SETFOCUS ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)
