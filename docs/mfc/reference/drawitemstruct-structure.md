---
title: DRAWITEMSTRUCT (Structure) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DRAWITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DRAWITEMSTRUCT structure [MFC]
ms.assetid: ba9ef1d4-aebb-45e9-b956-4b81a02e50f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff4596a52170d0c6d197a0bda431963b5f0e9344
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120932"
---
# <a name="drawitemstruct-structure"></a>DRAWITEMSTRUCT (structure)
La structure `DRAWITEMSTRUCT` fournit les informations que doit posséder la fenêtre propriétaire pour savoir comment dessiner un contrôle ou un élément de menu de type owner-drawn.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagDRAWITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    UINT itemID;  
    UINT itemAction;  
    UINT itemState;  
    HWND hwndItem;  
    HDC hDC;  
    RECT rcItem;  
    DWORD itemData;  
} DRAWITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Paramètres  
 *CtlType*  
 Type du contrôle. Les valeurs pour les types de contrôle sont les suivantes :  
  
- Bouton ODT_BUTTON Owner-drawn  
  
- Zone de liste déroulante Owner-drawn ODT_COMBOBOX  
  
- Zone de liste Owner-drawn odt_combobox  
  
- Menu ODT_MENU Owner-drawn  
  
- Contrôle ListView ODT_LISTVIEW  
  
- ODT_STATIC contrôle statique Owner-drawn  
  
- Contrôle onglet de ODT_TAB  
  
 *CtlID*  
 ID de contrôle pour une zone de liste modifiable, une zone de liste ou un bouton. Ce membre n’est pas utilisé pour un menu.  
  
 *ID d’élément*  
 ID d’élément de menu pour un menu ou index de l’élément d’une zone de liste ou d’une zone de liste modifiable. Pour une zone de liste vide ou une zone de liste modifiable, ce membre est une valeur négative, ce qui permet à l’application dessiner uniquement le rectangle de focus aux coordonnées spécifiées par le `rcItem` membre même s’il y a aucun élément dans le contrôle. L’utilisateur peut donc voir si la zone de liste ou la zone de liste modifiable a le focus d’entrée. Le paramètre des bits dans le `itemAction` membre détermine si le rectangle doit être dessiné comme si la zone de liste ou zone de liste modifiable a le focus.  
  
 *ItemAction*  
 Définit l’action de dessin nécessaire. Ce sera un ou plusieurs des bits suivants :  
  
- ODA_DRAWENTIRE ce bit est défini lors de l’ensemble du contrôle doit être dessiné.  
  
- ODA_FOCUS ce bit est défini lorsque le contrôle Obtient ou perd le focus d’entrée. Le `itemState` membre doit être vérifié pour déterminer si le contrôle a le focus.  
  
- ODA_SELECT ce bit est défini lorsque seul l’état de sélection a été modifiée. Le `itemState` membre doit être vérifié pour déterminer le nouvel état de sélection.  
  
 *itemState*  
 Spécifie l’état visuel de l’élément à l’issue de l’action de dessin en cours. Autrement dit, si un élément de menu doit être estompé, l’état indicateur ODS_GRAYED a la valeur. Les indicateurs d’état sont les suivants :  
  
- ODS_CHECKED ce bit est défini si l’élément de menu doit être vérifiée. Ce bit est utilisé uniquement dans un menu.  
  
- ODS_DISABLED ce bit est défini si l’élément doit être dessiné comme étant désactivé.  
  
- ODS_FOCUS ce bit est défini si l’élément a le focus d’entrée.  
  
- ODS_GRAYED ce bit est défini si l’élément doit être estompé. Ce bit est utilisé uniquement dans un menu.  
  
- ODS_SELECTED ce bit est défini si l’état de l’élément est sélectionné.  
  
- ODS_COMBOBOXEDIT le dessin prend place dans le champ de sélection (contrôle d’édition) d’une zone de liste modifiable de type owner-drawn.  
  
- ODS_DEFAULT l’élément est l’élément par défaut.  
  
 *hwndItem*  
 Spécifie le handle de fenêtre du contrôle pour les zones de liste modifiable, les zones de liste et les boutons. Spécifie le handle du menu (HMENU) qui contient l’élément pour les menus.  
  
 *hDC*  
 Identifie un contexte de périphérique. Le contexte de périphérique doit être utilisé au moment d’effectuer des opérations de dessin sur le contrôle.  
  
 *rcItem*  
 Un rectangle dans le contexte de périphérique spécifié par le *hDC* membre qui définit les limites du contrôle à dessiner. Windows détoure automatiquement tout ce que le propriétaire dessine dans le contexte de périphérique pour les zones de liste modifiable, les zones de liste et les boutons, mais il ne détoure pas les éléments de menu. Lors du dessin des éléments de menu, le propriétaire ne doit pas dessiner hors des limites du rectangle défini par le `rcItem` membre.  
  
 *itemData*  
 Pour une zone de liste modifiable ou une zone de liste, ce membre contient la valeur qui été passée à la zone de liste par l’une des méthodes suivantes :  
  
- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)  
  
- [CComboBox::AddString](../../mfc/reference/clistbox-class.md#addstring)  
  
- [CComboBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)  
  
 Pour un menu, ce membre contient la valeur qui été passée au menu par l’une des méthodes suivantes :  
  
- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)  
  
- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)  
  
- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)  
  
## <a name="remarks"></a>Notes  
 La fenêtre propriétaire de l’élément de contrôle ou du menu owner-drawn reçoit un pointeur vers cette structure comme le *lParam* paramètre du message WM_DRAWITEM.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** winuser.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

