---
title: Cmfcpropertygridtooltipctrl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 574da3d370a403aa74ba8c438b7c175bee19f198
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211963"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>Cmfcpropertygridtooltipctrl, classe
Implémente une info-bulle de contrôle qui le [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) utilise pour afficher des info-bulles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Construit un objet `CMFCPropertyGridToolTipCtrl`.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Crée une fenêtre pour le contrôle d’info-bulle.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Désactive et masque le contrôle d’info-bulle.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Retourne les coordonnées de la dernière position du contrôle d’info-bulle.|  
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Masque le contrôle d’info-bulle.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utilisé par la classe [CWinApp](../../mfc/reference/cwinapp-class.md) pour traduire les messages de fenêtre avant qu’ils soient distribués à le [TranslateMessage](https://msdn.microsoft.com/library/windows/desktop/ms644955) et [DispatchMessage](https://msdn.microsoft.com/library/windows/desktop/ms644934) des fonctions de Windows. (Substitue [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Définit l’espacement entre le texte d’info-bulle et la bordure de la fenêtre d’info-bulle.|  
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Affiche le contrôle d’info-bulle.|  
  
## <a name="remarks"></a>Notes  
 Info-bulles sont affichent lorsque le pointeur se trouve sur un nom de propriété. Le [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) classe affiche une info-bulle afin qu’elles soient facilement lisibles par l’utilisateur. En règle générale, la position d’une info-bulle est déterminée par la position du pointeur. À l’aide de cette classe, l’info-bulle s’affiche sur le nom de propriété et ressemble à l’extension naturelle de propriété, afin que le nom de propriété est entièrement visible.  
  
 MFC crée ce contrôle automatiquement et l’utilise dans le [classe CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un objet de la `CMFCPropertyGridToolTipCtrl` classe et comment afficher le contrôle d’info-bulle.  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxpropertygridtooltipctrl.h  
  
##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl  
 Construit un objet `CMFCPropertyGridToolTipCtrl`.  
  
```  
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```  
  
##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create  
 Crée une fenêtre pour le contrôle d’info-bulle.  
  
```  
BOOL Create(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pWndParent*  
 Pointeur vers la fenêtre parente.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la fenêtre a été créée avec succès ; Sinon, FALSE.  
  
##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate  
 Désactive et masque le contrôle d’info-bulle.  
  
```  
void Deactivate();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit la dernière position et texte sur des valeurs vides, afin que les appels à venir [CMFCPropertyGridToolTipCtrl::Track](#track) afficher l’info-bulle.  
  
##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect  
 Retourne les coordonnées de la dernière position du contrôle d’info-bulle.  
  
```  
void GetLastRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [out] *rect*  
 Contient la dernière position du contrôle d’info-bulle.  
  
##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide  
 Masque le contrôle d’info-bulle.  
  
```  
void Hide();
```  
  
##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin  
 Définit l’espacement entre le texte d’info-bulle et la bordure de la fenêtre d’info-bulle.  
  
```  
void SetTextMargin(int nTextMargin);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nTextMargin*  
 Spécifie l’espacement entre le texte info-bulle du contrôle et la bordure de la fenêtre d’info-bulle. La valeur par défaut est 10 pixels.  
  
##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track  
 Affiche le contrôle d’info-bulle.  
  
```  
void Track(
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
 Spécifie la position et la taille du contrôle d’info-bulle.  
  
 [in] *strText*  
 Spécifie le texte à afficher dans l’info-bulle.  
  
### <a name="remarks"></a>Notes  
 Cette méthode affiche le contrôle d’info-bulle à la position et la taille spécifiée par *rect*. Si la position, la taille et le texte n’ont pas changé depuis la dernière fois que cette méthode a été appelée, cette méthode n’a aucun effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
