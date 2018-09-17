---
title: Ctooltipmanager, classe | Microsoft Docs
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
ms.openlocfilehash: 81e027108d0f7b62ba707718c5396432396bdc5e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711878"
---
# <a name="ctooltipmanager-class"></a>Ctooltipmanager, classe
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
 Utilisez [CMFCToolTipCtrl, classe](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo`, et `CTooltipManager` pour implémenter des info-bulles personnalisées dans votre application. Pour obtenir un exemple montrant comment utiliser ces classes d’info-bulle, consultez le [CMFCToolTipCtrl, classe](../../mfc/reference/cmfctooltipctrl-class.md) rubrique.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)  
  
## <a name="requirements"></a>Configuration requise  
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
*pToolTip*<br/>
[out] Une référence à un pointeur d’info-bulle. Il est défini pour pointer vers l’info-bulle qui vient d’être créée lorsque la fonction retourne.  
  
*pWndParent*<br/>
[in] Parent de l’info-bulle.  
  
*%nLes*<br/>
[in] Type de l’info-bulle.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une info-bulle a été créée avec succès.  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler [CTooltipManager::DeleteToolTip](#deletetooltip) pour supprimer le contrôle d’info-bulle qui a été renvoyé dans *pToolTip*.  
  
 Le [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) définit les paramètres d’affichage visuel de chaque info-bulle, il crée en fonction de l’info-bulle type *%nLes* spécifie. Pour modifier les paramètres pour un ou plusieurs types d’info-bulle, appelez [CTooltipManager::SetTooltipParams](#settooltipparams).  
  
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
*pToolTip*<br/>
[in, out] Une référence à un pointeur vers une info-bulle à détruire.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour chaque [classe CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) qui a été créé par [CTooltipManager::CreateToolTip](#createtooltip). Le contrôle parent doit appeler cette méthode à partir de son `OnDestroy` gestionnaire. Cela est nécessaire pour supprimer correctement l’info-bulle à partir de l’infrastructure. Cette méthode définit *pToolTip* avec la valeur NULL avant de retourner.  
  
##  <a name="settooltipparams"></a>  CTooltipManager::SetTooltipParams  
 Personnalise l’apparence du contrôle d’info-bulle pour les types de contrôle Windows spécifiés.  
  
```  
void SetTooltipParams(
    UINT nTypes,  
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),  
    CMFCToolTipInfo* pParams=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
*nTypes*<br/>
[in] Spécifie les types de contrôle.  
  
*pRTC*<br/>
[in] Classe d’exécution de l’info-bulle personnalisée.  
  
*pParams*<br/>
[in] Paramètres de l’info-bulle.  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit la classe d’exécution et les paramètres initiaux qui le [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utilise lorsqu’il crée des info-bulles. Lorsqu’un contrôle appelle [CTooltipManager::CreateToolTip](#createtooltip) et passe dans une info-bulle de type qui est un des types indiqués par *nTypes*, le Gestionnaire d’info-bulle crée un contrôle d’info-bulle qui est une instance de la classe d’exécution spécifié par *pRTC* et transmet les paramètres spécifiés par *pParams* pour l’info-bulle de nouveau.  
  
 Lorsque vous appelez cette méthode, tous les propriétaires d’info-bulle existant le message d’AFX_WM_UPDATETOOLTIPS et ils doivent recréer leurs info-bulles à l’aide de [CTooltipManager::CreateToolTip](#createtooltip).  
  
 *nTypes* peut être n’importe quelle combinaison de l’info-bulle valide des types qui [CTooltipManager::CreateToolTip](#createtooltip) utilise, ou il peut être AFX_TOOLTIP_TYPE_ALL. Si vous transmettez AFX_TOOLTIP_TYPE_ALL, tous les types d’info-bulle sont affectés.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser le `SetTooltipParams` méthode de la `CTooltipManager` classe. Cet extrait de code fait partie de l’ [exemple Draw Client](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]  
  
##  <a name="settooltiptext"></a>  CTooltipManager::SetTooltipText  
 Définit le texte et la description pour une info-bulle.  
  
```  
static void SetTooltipText(
    TOOLINFO* pTI,  
    CToolTipCtrl* pToolTip,  
    UINT nType,  
    const CString strText,  
    LPCTSTR lpszDescr=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
*PTI*<br/>
[in] Pointeur vers un objet TOOLINFO.  
  
*pToolTip*<br/>
[in, out] Pointeur vers le contrôle d’info-bulle pour lequel définir le texte et la description.  
  
*%nLes*<br/>
[in] Spécifie le type de contrôle à laquelle cette info-bulle est associée.  
  
*strText*<br/>
[in] Texte à définir en tant que le texte d’info-bulle.  
  
*lpszDescr*<br/>
[in] Pointeur vers la description de l’info-bulle. Peut être NULL.  
  
### <a name="remarks"></a>Notes  
 La valeur de *%nLes* doit être la même valeur que la *%nLes* paramètre de [CTooltipManager::CreateToolTip](#createtooltip) lors de la création de l’info-bulle.  
  
##  <a name="updatetooltips"></a>  CTooltipManager::UpdateTooltips  
 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
```  
void UpdateTooltips();
```  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCToolTipCtrl, classe](../../mfc/reference/cmfctooltipctrl-class.md)   
 [CMFCToolTipInfo, classe](../../mfc/reference/cmfctooltipinfo-class.md)
