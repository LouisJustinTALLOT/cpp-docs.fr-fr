---
title: Drawitemstruct, Structure | Microsoft Docs
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
ms.openlocfilehash: 632f1b8b975c73c4f8a708ddb9efd64ce0cae015
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427249"
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

*CtlType*<br/>
Type du contrôle. Les valeurs pour les types de contrôle sont les suivantes :

- Bouton Owner-drawn de ODT_BUTTON

- Zone de liste déroulante Owner-drawn ODT_COMBOBOX

- Zone de liste Owner-drawn odt_combobox

- Menu de Owner-drawn ODT_MENU

- Contrôle ODT_LISTVIEW List view

- ODT_STATIC Owner-drawn un contrôle statique

- Contrôle d’onglet de ODT_TAB

*CtlID*<br/>
ID de contrôle pour une zone de liste modifiable, une zone de liste ou un bouton. Ce membre n’est pas utilisé pour un menu.

*itemID*<br/>
ID d’élément de menu pour un menu ou index de l’élément d’une zone de liste ou d’une zone de liste modifiable. Pour une zone de liste vide ou une zone de liste modifiable, ce membre est une valeur négative, ce qui permet l’application de dessiner uniquement le rectangle de focus aux coordonnées spécifiées par le `rcItem` membre même s’il y a aucun élément dans le contrôle. L’utilisateur peut donc voir si la zone de liste ou la zone de liste modifiable a le focus d’entrée. Le paramètre des bits dans le `itemAction` membre détermine si le rectangle doit être dessiné comme si la zone de liste ou une zone de liste modifiable a le focus.

*itemAction*<br/>
Définit l’action de dessin nécessaire. Ce sera un ou plusieurs des bits suivants :

- ODA_DRAWENTIRE ce bit est défini lors de l’ensemble du contrôle doit être dessiné.

- ODA_FOCUS ce bit est défini lorsque le contrôle Obtient ou perd le focus d’entrée. Le `itemState` membre doit être vérifié pour déterminer si le contrôle a le focus.

- ODA_SELECT ce bit est défini lorsque seul l’état de sélection a changé. Le `itemState` membre doit être vérifié pour déterminer le nouvel état de sélection.

*itemState*<br/>
Spécifie l’état visuel de l’élément à l’issue de l’action de dessin en cours. Autrement dit, si un élément de menu doit être estompé, l’indicateur d’état ODS_GRAYED sera être définie. Les indicateurs d’état sont les suivants :

- ODS_CHECKED ce bit est défini si l’élément de menu doit être vérifiée. Ce bit est utilisé uniquement dans un menu.

- ODS_DISABLED ce bit est défini si l’élément doit être dessiné comme étant désactivé.

- ODS_FOCUS ce bit est défini si l’élément a le focus d’entrée.

- ODS_GRAYED ce bit est défini si l’élément doit être estompé. Ce bit est utilisé uniquement dans un menu.

- ODS_SELECTED ce bit est défini si l’état de l’élément est sélectionné.

- ODS_COMBOBOXEDIT le dessin s’effectue dans le champ de sélection (contrôle d’édition) d’une zone de liste modifiable de type owner-drawn.

- ODS_DEFAULT l’élément est l’élément par défaut.

*hwndItem*<br/>
Spécifie le handle de fenêtre du contrôle pour les zones de liste modifiable, les zones de liste et les boutons. Spécifie le handle du menu (HMENU) qui contient l’élément pour les menus.

*hDC*<br/>
Identifie un contexte de périphérique. Le contexte de périphérique doit être utilisé au moment d’effectuer des opérations de dessin sur le contrôle.

*rcItem*<br/>
Un rectangle dans le contexte de périphérique spécifié par le *hDC* membre qui définit les limites du contrôle à dessiner. Windows détoure automatiquement tout ce que le propriétaire dessine dans le contexte de périphérique pour les zones de liste modifiable, les zones de liste et les boutons, mais il ne détoure pas les éléments de menu. Lors du dessin des éléments de menu, le propriétaire ne doit pas dessiner en dehors des limites du rectangle défini par le `rcItem` membre.

*itemData*<br/>
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

La fenêtre propriétaire de l’élément de menu ou de contrôle owner-drawn reçoit un pointeur vers cette structure en tant que le *lParam* paramètre du message WM_DRAWITEM.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem)

