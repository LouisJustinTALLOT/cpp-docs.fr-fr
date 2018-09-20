---
title: Measureitemstruct, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MEASUREITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db24d772e2f007b3350443ae6bc84f97cac34e76
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397765"
---
# <a name="measureitemstruct-structure"></a>MEASUREITEMSTRUCT, structure

Le `MEASUREITEMSTRUCT` structure informe Windows des dimensions d’un élément de menu ou de contrôle owner-drawn.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagMEASUREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemWidth;
    UINT itemHeight;
    DWORD itemData
} MEASUREITEMSTRUCT;
```

#### <a name="parameters"></a>Paramètres

*CtlType*<br/>
Contient le type de contrôle. Les valeurs pour les types de contrôle sont les suivantes :

- Zone de liste déroulante Owner-draw ODT_COMBOBOX

- Zone de liste Owner-draw odt_combobox

- Menu du mode Owner-draw ODT_MENU

*CtlID*<br/>
Contient l’ID de contrôle pour une zone de liste déroulante, une zone de liste ou un bouton. Ce membre n’est pas utilisé pour un menu.

*itemID*<br/>
Contient l’ID d’élément de menu pour un menu ou l’ID d’élément de zone de liste pour une zone de liste déroulante de hauteur variable ou d’une zone de liste. Ce membre n’est pas utilisé pour une zone de liste déroulante de hauteur fixe ou de la zone de liste, ou pour un bouton.

*itemWidth*<br/>
Spécifie la largeur d’un élément de menu. Le propriétaire de l’élément de menu en mode owner-draw doit remplir ce membre avant de retourner à partir du message.

*itemHeight*<br/>
Spécifie la hauteur d’un élément individuel dans une zone de liste ou un menu. Avant de retourner à partir du message, le propriétaire de la zone de liste déroulante owner-draw, zone de liste, ou élément de menu doit remplir ce membre. La hauteur maximale d’un élément de zone de liste est 255.

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

Cela permet à Windows traiter correctement les interactions utilisateur avec le contrôle. Échec de remplir les membres appropriés dans le `MEASUREITEMSTRUCT` structure entraîne des opérations incorrectes du contrôle.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

