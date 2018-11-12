---
title: COMPAREITEMSTRUCT, structure
ms.date: 11/04/2016
f1_keywords:
- COMPAREITEMSTRUCT
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
ms.openlocfilehash: 78a6e76ee3bbac5b32eb4bccf45578e63f763b75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465414"
---
# <a name="compareitemstruct-structure"></a>COMPAREITEMSTRUCT, structure

Le `COMPAREITEMSTRUCT` structure fournit les identificateurs et les données de fournie par l’application pour les deux éléments dans une zone de liste triée, owner-drawn ou de la zone de liste déroulante.

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

*CtlType*<br/>
Odt_combobox (qui spécifie une zone de liste owner-draw) ou ODT_COMBOBOX (qui spécifie une zone de liste déroulante owner-draw).

*CtlID*<br/>
L’ID de contrôle pour la zone de liste ou une zone de liste déroulante.

*hwndItem*<br/>
Le handle de fenêtre du contrôle.

*itemID1*<br/>
L’index du premier élément dans la zone de liste ou une zone de liste déroulante qui est comparée.

*itemData1*<br/>
Données fournie par l’application pour le premier élément qui est comparée. Cette valeur a été passée dans l’appel qui a ajouté l’élément à la zone de liste déroulante ou liste.

*itemID2*<br/>
Index du deuxième élément dans la zone de liste ou une zone de liste déroulante qui est comparée.

*itemData2*<br/>
Données fournie par l’application pour le deuxième élément qui est comparée. Cette valeur a été passée dans l’appel qui a ajouté l’élément à la zone de liste déroulante ou liste.

## <a name="remarks"></a>Notes

Chaque fois qu’une application ajoute un nouvel élément à une zone de liste owner-drawn ou d’une zone de liste déroulante créée avec le style CBS_SORT ou LBS_SORT, Windows envoie un message WM_COMPAREITEM au propriétaire. Le *lParam* paramètre du message contient un pointeur long désignant un `COMPAREITEMSTRUCT` structure. Lorsqu’il reçoit le message, le propriétaire compare les deux éléments et retourne une valeur indiquant quel élément trie avant les autres.

## <a name="requirements"></a>Configuration requise

**En-tête :** winuser.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

