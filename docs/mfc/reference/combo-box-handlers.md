---
title: Gestionnaires de zone de liste déroulante
ms.date: 11/04/2016
f1_keywords:
- ON_CBN_KILLFOCUS
- ON_CBN_ERRSPACE
- ON_CBN_EDITCHANGE
- ON_CBN_CLOSEUP
- ON_CBN_DBLCLK
- ON_CBN_EDITUPDATE
- ON_CBN_DROPDOWN
- ON_CBN_SELENDOK
- ON_CBN_SELCHANGE
- ON_CBN_SETFOCUS
- ON_CBN_SELENDCANCEL
helpviewer_keywords:
- ON_CBN_CLOSEUP
- ON_CBN_SETFOCUS
- ON_CBN_DBLCLK
- ON_CBN_SELENDCANCEL
- ON_CBN_DROPDOWN
- ON_CBN_EDITUPDATE
- ON_CBN_KILLFOCUS
- combo boxes [MFC], handlers
- ON_CBN_EDITCHANGE
- ON_CBN_ERRSPACE
- ON_CBN_SELENDOK
- ON_CBN_SELCHANGE
ms.assetid: 7f092412-01b7-4242-95ec-41ba506b9d71
ms.openlocfilehash: ed83bcf565ec420d159c73ddfd82827aac88693f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259436"
---
# <a name="combo-box-handlers"></a>Gestionnaires de zone de liste déroulante

Les entrées de mappage suivantes correspondent aux prototypes de fonction.

|Entrée de mappage|Prototype de fonction|
|---------------|------------------------|
|ON_CBN_CLOSEUP( \<id>, \<memberFxn> )|afx_msg void memberFxn( )|
|ON_CBN_DBLCLK( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_DROPDOWN( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_EDITCHANGE ( \<id >, \<memberFxn >)|afx_msg void memberFxn( );|
|ON_CBN_EDITUPDATE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_ERRSPACE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_KILLFOCUS( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_SELCHANGE( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_SELENDCANCEL( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_SELENDOK( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|
|ON_CBN_SETFOCUS( \<id>, \<memberFxn> )|afx_msg void memberFxn( );|

## <a name="see-also"></a>Voir aussi

[Tables des messages](../../mfc/reference/message-maps-mfc.md)
