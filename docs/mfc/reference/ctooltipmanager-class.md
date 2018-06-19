---
title: Classe de CTooltipManager | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
dev_langs:
- C++
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78b191766e33d291317ef50a4d5373dc26428577
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372178"
---
# <a name="ctooltipmanager-class"></a>Classe de CTooltipManager
Gère les informations d'exécution relatives aux info-bulles. La classe `CTooltipManager` est instanciée une fois par application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CTooltipManager : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CTooltipManager::CreateToolTip](#createtooltip)|Crée un contrôle d'info-bulle pour les types de contrôles Windows spécifiés.|  
|[CTooltipManager::DeleteToolTip](#deletetooltip)|Supprime un contrôle d'info-bulle.|  
|[CTooltipManager::SetTooltipParams](#settooltipparams)|Personnalise l'apparence visuelle du contrôle d'info-bulle pour les types de contrôles Windows spécifiés.|  
|[CTooltipManager::SetTooltipText](#settooltiptext)|Définit le texte et la description d'un contrôle d'info-bulle.|  
|[CTooltipManager::UpdateTooltips](#updatetooltips)||  
  
## <a name="remarks"></a>Notes  
 Utilisez [CMFCToolTipCtrl classe](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, et `CTooltipManager` pour implémenter des info-bulles personnalisées dans votre application. Pour obtenir un exemple montrant comment utiliser ces classes d’info-bulle, consultez le [CMFCToolTipCtrl classe](../../mfc/reference/cmfctooltipctrl-class.md) rubrique.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxtooltipmanager.h  
  
##  <a name="createtooltip"></a>  CTooltipManager::CreateToolTip  
 Crée un contrôle d’info-bulle.  
  
```  
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,  
    CWnd* pWndParent,  
    UINT nType);
```  
  
### <a name="parameters"></a>Paramètres  
 [out] `pToolTip`  
 Une référence à un pointeur d’info-bulle. Il est configuré pour pointer vers l’info-bulle qui vient d’être créée lorsque la fonction retourne.  
  
 [in] `pWndParent`  
 Parent de l’info-bulle.  
  
 [in] `nType`  
 Type de l’info-bulle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une info-bulle a été créée avec succès.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler [CTooltipManager::DeleteToolTip](#deletetooltip) pour supprimer le contrôle d’info-bulle qui a été retourné dans `pToolTip`.  
  
 Le [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) de type qui définit les paramètres d’affichage de chaque info-bulle, il crée en fonction de l’info-bulle `nType` spécifie. Pour modifier les paramètres pour un ou plusieurs types d’info-bulle, appelez [CTooltipManager::SetTooltipParams](#settooltipparams).  
  
 Types de l’info-bulle valides sont répertoriés dans le tableau suivant :  
  
|Type de l’info-bulle|Catégorie de contrôle|Exemples de types|  
|------------------|----------------------|-------------------|  
|AFX_TOOLTIP_TYPE_BUTTON|Un bouton.|CMFCButton|  
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Une barre de légende.|CMFCCaptionBar|  
|AFX_TOOLTIP_TYPE_DEFAULT|N’importe quel contrôle qui ne correspond pas à une autre catégorie.|Aucun.|  
|AFX_TOOLTIP_TYPE_DOCKBAR|Un volet Ancrable.|CDockablePane|  
|AFX_TOOLTIP_TYPE_EDIT|Une zone de texte.|Aucun.|  
|AFX_TOOLTIP_TYPE_MINIFRAME|Un mini-frame.|CPaneFrameWnd|  
|AFX_TOOLTIP_TYPE_PLANNER|Un planificateur.|Aucun.|  
|AFX_TOOLTIP_TYPE_RIBBON|Une barre de ruban.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|  
|AFX_TOOLTIP_TYPE_TAB|Un contrôle onglet.|CMFCTabCtrl|  
|AFX_TOOLTIP_TYPE_TOOLBAR|Une barre d’outils.|CMFCToolBar, CMFCPopupMenuBar|  
|AFX_TOOLTIP_TYPE_TOOLBOX|Une boîte à outils.|Aucun.|  
  
##  <a name="deletetooltip"></a>  CTooltipManager::DeleteToolTip  
 Supprime un contrôle d'info-bulle.  
  
```  
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```  
  
### <a name="parameters"></a>Paramètres  
 [in, out] `pToolTip`  
 Une référence à un pointeur vers une info-bulle d’être détruites.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour chaque [CToolTipCtrl (classe)](../../mfc/reference/ctooltipctrl-class.md) qui a été créé par [CTooltipManager::CreateToolTip](#createtooltip). Le contrôle parent doit appeler cette méthode à partir de son `OnDestroy` gestionnaire. Cela est nécessaire pour supprimer correctement l’info-bulle de l’infrastructure. Cette méthode définit `pToolTip` à `NULL` avant d’être retournée.  
  
##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams  
 Personnalise l’apparence du contrôle d’info-bulle pour les types de contrôles Windows spécifiés.  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nTypes`  
 Spécifie les types de contrôle.  
  
 [in] `pRTC`  
 Classe d’exécution de l’info-bulle personnalisée.  
  
 [in] `pParams`  
 Paramètres de l’info-bulle.  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit la classe d’exécution et les paramètres initiaux qui le [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utilise lorsqu’il crée des info-bulles. Lorsqu’un contrôle appelle [CTooltipManager::CreateToolTip](#createtooltip) et passe dans une info-bulle de type qui est un des types indiqués par `nTypes`, le Gestionnaire d’info-bulle crée un contrôle d’info-bulle qui est une instance de la classe runtime spécifiée par `pRTC` et transmet les paramètres spécifiés par `pParams` pour l’info-bulle de nouveau.  
  
 Lorsque vous appelez cette méthode, le message AFX_WM_UPDATETOOLTIPS de réception de tous les propriétaires d’info-bulle existant et doit recréer les info-bulles à l’aide de [CTooltipManager::CreateToolTip](#createtooltip).  
  
 `nTypes` peut être n’importe quelle combinaison de l’info-bulle valide les types qui [CTooltipManager::CreateToolTip](#createtooltip) utilise, ou il peut être AFX_TOOLTIP_TYPE_ALL. Si vous passez AFX_TOOLTIP_TYPE_ALL, tous les types d’info-bulle sont affectées.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `SetTooltipParams` méthode de la `CTooltipManager` classe. Cet extrait de code fait partie de l’ [exemple Draw Client](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText  
 Définit le texte et la description d’une info-bulle.  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pTI`  
 Pointeur vers un objet TOOLINFO.  
  
 [in, out] `pToolTip`  
 Pointeur vers le contrôle d’info-bulle pour lequel définir le texte et la description.  
  
 [in] `nType`  
 Spécifie le type de contrôle auquel cette info-bulle est associée.  
  
 [in] `strText`  
 Texte à définir en tant que le texte d’info-bulle.  
  
 [in] `lpszDescr`  
 Pointeur vers la description de l’info-bulle. Peut être `NULL`.  
  
### <a name="remarks"></a>Notes  
 La valeur de `nType` doit être la même valeur que la `nType` paramètre de [CTooltipManager::CreateToolTip](#createtooltip) lors de la création de l’info-bulle.  
  
##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe de CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo, classe](../../mfc/reference/cmfctooltipinfo-class.md)
