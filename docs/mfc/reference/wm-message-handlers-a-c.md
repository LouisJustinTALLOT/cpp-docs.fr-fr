---
title: "WM_, gestionnaires de messages&#160;: A - C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ON_WM_CREATE"
  - "ON_WM_COMPACTING"
  - "ON_WM_CHARTOITEM"
  - "ON_WM_ASKCBFORMATNAME"
  - "ON_WM_CTLCOLOR"
  - "ON_WM_COMPAREITEM"
  - "ON_WM_CHILDACTIVATE"
  - "ON_WM_CONTEXTMENU"
  - "ON_WM_ACTIVATE"
  - "ON_WM_CANCELMODE"
  - "ON_WM_CLOSE"
  - "ON_WM_CAPTURECHANGED"
  - "ON_WM_ACTIVATEAPP"
  - "ON_WM_CHAR"
  - "ON_WM_CHANGECBCHAIN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ON_WM_ACTIVATE"
  - "ON_WM_ACTIVATEAPP"
  - "ON_WM_ASKCBFORMATNAME"
  - "ON_WM_CANCELMODE"
  - "ON_WM_CAPTURECHANGED"
  - "ON_WM_CHANGECBCHAIN"
  - "ON_WM_CHAR"
  - "ON_WM_CHARTOITEM"
  - "ON_WM_CHILDACTIVATE"
  - "ON_WM_CLOSE"
  - "ON_WM_COMPACTING"
  - "ON_WM_COMPAREITEM"
  - "ON_WM_CONTEXTMENU"
  - "ON_WM_CREATE"
  - "ON_WM_CTLCOLOR"
  - "WM_ (messages)"
ms.assetid: 4e315896-d646-4b87-b0ab-41a4a753b045
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# WM_, gestionnaires de messages&#160;: A - C
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Les entrées de mappage suivantes à gauche correspondent aux prototypes de fonctions à droite :  
  
|Entrée de mappage|Prototype de fonction|  
|-----------------------|---------------------------|  
|ON\_WM\_ACTIVATE\(\)|afx\_msg void [OnActivate](../Topic/CWnd::OnActivate.md)\(UINT, CWnd\*, BOOL\);|  
|ON\_WM\_ACTIVATEAPP\(\)|afx\_msg void [OnActivateApp](../Topic/CWnd::OnActivateApp.md)\(BOOL, DWORD\);|  
|ON\_WM\_APPCOMMAND\(\)|afx\_msg void [OnAppCommand](../Topic/CWnd::OnAppCommand.md)\(CWnd\*, UINT, UINT, UINT\);|  
|ON\_WM\_ASKCBFORMATNAME\(\)|afx\_msg void [OnAskCbFormatName](../Topic/CWnd::OnAskCbFormatName.md)\(UINT, LPSTR\);|  
|ON\_WM\_CANCELMODE\(\)|afx\_msg void [OnCancelMode](../Topic/CWnd::OnCancelMode.md)\(\);|  
|ON\_WM\_CAPTURECHANGED\(\)|afx\_msg void [OnCaptureChanged](../Topic/CWnd::OnCaptureChanged.md)\(CWnd\*\);|  
|ON\_WM\_CHANGECBCHAIN\(\)|afx\_msg void [OnChangeCbChain](../Topic/CWnd::OnChangeCbChain.md)\(HWND, HWND\);|  
|ON\_WM\_CHAR\(\)|afx\_msg void [OnChar](../Topic/CWnd::OnChar.md)\(UINT, UINT, UINT\);|  
|ON\_WM\_CHARTOITEM\(\)|afx\_msg int [OnCharToItem](../Topic/CWnd::OnCharToItem.md)\(UINT, CWnd\*, UINT\);|  
|ON\_WM\_CHILDACTIVATE\(\)|afx\_msg void [OnChildActivate](../Topic/CWnd::OnChildActivate.md)\(\);|  
|ON\_WM\_CLIPBOARDUPDATE\(\)|afx\_msg void [OnClipboardUpdate](../Topic/CWnd::OnClipboardUpdate.md)\(\);|  
|ON\_WM\_CLOSE\(\)|afx\_msg void [OnClose](../Topic/CWnd::OnClose.md)\(\);|  
|ON\_WM\_COMPACTING\(\)|afx\_msg void [OnCompacting](../Topic/CWnd::OnCompacting.md)\(UINT\);|  
|ON\_WM\_COMPAREITEM\(\)|afx\_msg int [OnCompareItem](../Topic/CWnd::OnCompareItem.md)\(LPCOMPAREITEMSTRUCT\);|  
|ON\_WM\_CONTEXTMENU\(\)|afx\_msg void [OnContextMenu](../Topic/CWnd::OnContextMenu.md)\(CWnd\*, CPoint\);|  
|ON\_WM\_COPYDATA\(\)|afx\_msg BOOL [OnCopyData](../Topic/CWnd::OnCopyData.md)\(CWnd\* pWnd, COPYDATASTRUCT\* pCopyDataStruct\);|  
|ON\_WM\_CREATE\(\)|afx\_msg int [OnCreate](../Topic/CWnd::OnCreate.md)\(LPCREATESTRUCT\);|  
|ON\_WM\_CTLCOLOR\(\)|afx\_msg HBRUSH [OnCtlColor](../Topic/CWnd::OnCtlColor.md)\(CDC\*, CWnd\*, UINT\);|  
  
## Voir aussi  
 [Tables des messages](../../mfc/reference/message-maps-mfc.md)   
 [Gestionnaires de messages WM\_](../../mfc/reference/handlers-for-wm-messages.md)