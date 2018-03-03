---
title: COMPAREITEMSTRUCT (Structure) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COMPAREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7903e51a83533c8f2458c4400c64717021a1ccb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT, structure
Le `COMPAREITEMSTRUCT` structure fournit les identificateurs et les données de fournie par l’application pour les deux éléments dans une zone de liste triée, owner-drawn ou d’une zone de liste déroulante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `CtlType`  
 **Odt_combobox** (qui spécifie une zone de liste owner-draw) ou **ODT_COMBOBOX** (qui spécifie une zone de liste déroulante owner-draw).  
  
 `CtlID`  
 L’ID de contrôle pour la zone de liste ou zone de liste déroulante.  
  
 `hwndItem`  
 Le handle de fenêtre du contrôle.  
  
 *itemID1*  
 L’index du premier élément dans la zone de liste ou zone de liste déroulante qui sont comparés.  
  
 *itemData1*  
 Données fournie par l’application pour le premier élément qui est comparée. Cette valeur a été passée dans l’appel qui a ajouté l’élément à la zone de liste déroulante ou liste.  
  
 *itemID2*  
 Index du deuxième élément dans la zone de liste ou zone de liste déroulante qui sont comparés.  
  
 *itemData2*  
 Données fournie par l’application pour le second élément comparé. Cette valeur a été passée dans l’appel qui a ajouté l’élément à la zone de liste déroulante ou liste.  
  
## <a name="remarks"></a>Notes  
 Chaque fois qu’une application ajoute un nouvel élément à une zone de liste owner-drawn ou zone de liste modifiable est créé avec le **CBS_SORT** ou **LBS_SORT** style, Windows envoie le propriétaire une `WM_COMPAREITEM` message. Le `lParam` paramètre du message contient un pointeur long vers un `COMPAREITEMSTRUCT` structure. Lorsqu’il reçoit le message, le propriétaire compare les deux éléments et retourne une valeur qui indique quel élément trie avant l’autre.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

