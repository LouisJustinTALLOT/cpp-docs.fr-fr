---
title: IView Interface | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a06243af3de7a2f4b32aa9a9ae492dfe3b2d3b64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370957"
---
# <a name="iview-interface"></a>Interface de IView
Implémente plusieurs méthodes qui [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utilise pour envoyer des notifications d’affichage à un contrôle géré.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class IView  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|Appelé par MFC lorsqu’une vue est activée ou désactivée.|  
|[IView::OnInitialUpdate](#oninitialupdate)|Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.|  
|[IView::OnUpdate](#onupdate)|Appelée par MFC, une fois que le document de la vue a été modifié ; Cette fonction permet à la vue mettre à jour son affichage pour refléter les modifications.|  
  
## <a name="remarks"></a>Notes  
 `IView` implémente plusieurs méthodes qui `CWinFormsView` utilise pour transférer des notifications d’affichage pour un contrôle managé hébergé communes. Il s’agit [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) et [OnActivateView](#onactivateview).  
  
 `IView` est semblable à [CView](../../mfc/reference/cview-class.md), mais est utilisé uniquement avec les vues gérés et des contrôles.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  

## <a name="requirements"></a>Spécifications  
 En-tête : les afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)  

## <a name="onactivateview"></a> IView::OnActivateView  
Appelé par MFC lorsqu’une vue est activée ou désactivée.
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>Paramètres
`activate`  
Indique si la vue est activée ou désactivée.  

## <a name="oninitialupdate"></a> IView::OnInitialUpdate
Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate 
Appelé par MFC lorsque document de la vue a été modifié.  
```
void OnUpdate();
```
## <a name="remarks"></a>Notes  
Cette fonction permet à la vue mettre à jour son affichage pour refléter les modifications.

## <a name="see-also"></a>Voir aussi  
 [Classe CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [CView, classe](../../mfc/reference/cview-class.md)
