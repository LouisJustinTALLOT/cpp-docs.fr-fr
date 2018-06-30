---
title: DELETEITEMSTRUCT (Structure) | Documents Microsoft
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
ms.openlocfilehash: 5c844ad428143c82e8214eab74262b326bf2c9a4
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123238"
---
# <a name="deleteitemstruct-structure"></a>DELETEITEMSTRUCT, structure
Le `DELETEITEMSTRUCT` structure décrit un owner-drawn zone de liste ou zone de liste déroulante élément supprimé.  
  
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
 *CtlType*  
 Spécifie les odt_combobox (une zone de liste owner-drawn) ou ODT_COMBOBOX (une zone de liste déroulante owner-drawn).  
  
 *CtlID*  
 Spécifie l’identificateur de la zone de liste ou zone de liste déroulante.  
  
 *ID d’élément*  
 Spécifie l’index de l’élément dans la zone de liste ou zone de liste déroulante en cours de suppression.  
  
 *hwndItem*  
 Identifie le contrôle.  
  
 *itemData*  
 Spécifie les données définies par l’application pour l’élément. Cette valeur est passée au contrôle dans le *lParam* paramètre du message qui ajoute l’élément à la zone de liste ou zone de liste déroulante.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un élément est supprimé de la zone de liste ou zone de liste déroulante ou lorsque la zone de liste ou zone de liste déroulante est détruit, Windows envoie le message WM_DELETEITEM au propriétaire de chaque élément supprimé. Le *lParam* paramètre du message contient un pointeur vers cette structure.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atldbcli.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem)


