---
title: Deleteitemstruct, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DELETEITEMSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- DELETEITEMSTRUCT structure [MFC]
ms.assetid: 48d3998c-f4a8-402a-bf90-df3770a78685
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9061205bdf3697e492b846d160a5b4dd2d154bb9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065016"
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT, structure

Le `DELETEITEMSTRUCT` structure décrit un supprimé élément owner-drawn zone de liste ou zone de liste déroulante.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagDELETEITEMSTRUCT { /* ditms */
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    HWND hwndItem;
    UINT itemData;
} DELETEITEMSTRUCT;
```

#### <a name="parameters"></a>Paramètres

*CtlType*<br/>
Spécifie les odt_combobox (une zone de liste owner-drawn) ou ODT_COMBOBOX (une zone de liste déroulante owner-drawn).

*CtlID*<br/>
Spécifie l’identificateur de la zone de liste ou une zone de liste déroulante.

*itemID*<br/>
Spécifie l’index de l’élément dans la zone de liste ou une zone de liste déroulante en cours de suppression.

*hwndItem*<br/>
Identifie le contrôle.

*itemData*<br/>
Spécifie les données définies par l’application pour l’élément. Cette valeur est passée au contrôle dans le *lParam* paramètre du message qui ajoute l’élément à la zone de liste ou une zone de liste déroulante.

## <a name="remarks"></a>Notes

Lorsqu’un élément est supprimé à partir de la zone de liste ou une zone de liste déroulante ou lorsque la zone de liste ou une zone de liste déroulante est détruit, Windows envoie le message WM_DELETEITEM au propriétaire de chaque élément supprimé. Le *lParam* paramètre du message contient un pointeur vers cette structure.

## <a name="requirements"></a>Configuration requise

**En-tête :** atldbcli.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)

