---
description: 'En savoir plus sur : gestionnaires de bouton utilisateur'
title: Gestionnaires de bouton utilisateur
ms.date: 11/04/2016
f1_keywords:
- ON_BN_HILITE
- ON_BN_DOUBLECLICKED
- ON_BN_CLICKED
- ON_BN_PAINT
- ON_BN_DISABLE
- ON_BN_UNHILITE
helpviewer_keywords:
- ON_BN_PAINT
- user buttons [MFC]
- ON_BN_DOUBLECLICKED [MFC]
- ON_BN_DISABLE [MFC]
- ON_BN_UNHILITE [MFC]
- ON_BN_HILITE [MFC]
- ON_BN_CLICKED [MFC]
ms.assetid: 410ea968-478f-4806-b7b8-5d7c8dc2bf42
ms.openlocfilehash: 944ded857062979e4de4141275a1a80564f8df9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218587"
---
# <a name="user-button-handlers"></a>Gestionnaires de bouton utilisateur

Les entrées de mappage suivantes correspondent aux prototypes de fonction.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|ON_BN_CLICKED ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_BN_DISABLE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_BN_DOUBLECLICKED ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_BN_HILITE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_BN_PAINT ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|
|ON_BN_UNHILITE ( \<id> , \<memberFxn> )|afx_msg void memberFxn ();|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)
