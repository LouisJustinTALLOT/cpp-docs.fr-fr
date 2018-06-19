---
title: Classe de CMFCImageEditorPaletteBar | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::GetRowHeight
- AFXIMAGEEDITORDIALOG/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorPaletteBar [MFC], GetRowHeight
- CMFCImageEditorPaletteBar [MFC], IsButtonExtraSizeAvailable
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e377a465dd55d8940e74617130216220d03f1218
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370040"
---
# <a name="cmfcimageeditorpalettebar-class"></a>Classe de CMFCImageEditorPaletteBar
Fournit des fonctionnalités de barre de palette pour une image de boîte de dialogue de l’éditeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCImageEditorPaletteBar : public CMFCToolBar  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCImageEditorPaletteBar::GetRowHeight](#getrowheight)|Retourne la hauteur des boutons de barre d’outils. (Substitue [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Détermine si la barre d’outils peut afficher des boutons que vous avez étendu les bordures. (Substitue [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
  
### <a name="remarks"></a>Notes  
 Cette classe n’est pas destinée à être utilisée directement depuis votre code.  
  
 Le framework utilise cette classe pour afficher une barre de palette dans une boîte de dialogue Éditeur image. Pour plus d’informations sur la boîte de dialogue Éditeur image, consultez [CMFCImageEditorDialog classe](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afximageeditordialog.h  
  
##  <a name="getrowheight"></a>  CMFCImageEditorPaletteBar::GetRowHeight  
 Retourne la hauteur des boutons de barre d’outils.  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur de chaque bouton de la barre d’outils.  
  
##  <a name="isbuttonextrasizeavailable"></a>  CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable  
 Détermine si la barre d’outils peut afficher des boutons que vous avez étendu les bordures.  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne `FALSE`.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog, classe](../../mfc/reference/cmfcimageeditordialog-class.md)
