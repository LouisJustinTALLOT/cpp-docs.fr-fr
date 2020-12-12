---
description: 'En savoir plus sur : gestionnaires de contrôles d’édition'
title: Gestionnaires de contrôles d'édition
ms.date: 11/04/2016
f1_keywords:
- ON_EN_ERRSPACE
- ON_EN_UPDATE
- ON_EN_VSCROLL
- ON_EN_HSCROLL
- ON_EN_KILLFOCUS
- ON_EN_MAXTEXT
- ON_EN_SETFOCUS
- ON_EN_CHANGE
helpviewer_keywords:
- ON_EN_ERRSPACE macro [MFC]
- ON_EN_SETFOCUS macro [MFC]
- ON_EN_UPDATE macro [MFC]
- ON_EN_MAXTEXT macro [MFC]
- ON_EN_CHANGE macro [MFC]
- ON_EN_HSCROLL macro [MFC]
- ON_EN_VSCROLL macro [MFC]
- ON_EN_KILLFOCUS macro [MFC]
- edit controls [MFC], edit control handlers
ms.assetid: 55b88b5e-12b5-4422-b03e-c8c2f27d095c
ms.openlocfilehash: ee73dac1ae0c304c4a233532b1470cc696b8e00d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97219887"
---
# <a name="edit-control-handlers"></a>Gestionnaires de contrôles d'édition

Les entrées de mappage suivantes correspondent au prototype de fonction.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|ON_EN_CHANGE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_ERRSPACE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_HSCROLL ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_KILLFOCUS ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_MAXTEXT ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_SETFOCUS ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_UPDATE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_EN_VSCROLL ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)
