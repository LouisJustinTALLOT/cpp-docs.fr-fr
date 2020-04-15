---
title: Classe CTooltipManager
ms.date: 11/04/2016
f1_keywords:
- CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager
- AFXTOOLTIPMANAGER/CTooltipManager::CreateToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::DeleteToolTip
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipParams
- AFXTOOLTIPMANAGER/CTooltipManager::SetTooltipText
- AFXTOOLTIPMANAGER/CTooltipManager::UpdateTooltips
helpviewer_keywords:
- CTooltipManager [MFC], CreateToolTip
- CTooltipManager [MFC], DeleteToolTip
- CTooltipManager [MFC], SetTooltipParams
- CTooltipManager [MFC], SetTooltipText
- CTooltipManager [MFC], UpdateTooltips
ms.assetid: c71779d7-8b6e-47ef-8500-d4552731fe86
ms.openlocfilehash: 37fcf47b7537e89974a61e6c50c41e164d555678
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365076"
---
# <a name="ctooltipmanager-class"></a>Classe CTooltipManager

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
|[CTooltipManager::SetTooltipText](#updatetooltips)||

## <a name="remarks"></a>Notes

Utilisez [cmFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) `CMFCToolTipInfo`Class `CTooltipManager` , et ensemble pour implémenter des outils personnalisés dans votre application. Pour un exemple de la façon d’utiliser ces classes de pointe d’outil, voir le sujet de classe [CMFCToolTipCtrl.](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtooltipmanager.h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a>CTooltipManager::CreateToolTip

Crée un contrôle de bout d’outil.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Paramètres

*pToolTip*<br/>
[out] Une référence à un pointeur tooltip. Il est configuré pour pointer vers la pointe d’outils nouvellement créée lorsque la fonction revient.

*pWndParent*<br/>
[dans] Parent de l’outiltip.

*nType*<br/>
[dans] Type de l’outiltip.

### <a name="return-value"></a>Valeur de retour

Nonzero si un tooltip a été créé avec succès.

### <a name="remarks"></a>Notes

Vous devez appeler [CTooltipManager::DeleteToolTip](#deletetooltip) pour supprimer le contrôle de la pointe d’outil qui est passé en arrière dans *pToolTip*.

Le [CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) définit les paramètres d’affichage visuel de chaque outil qu’il crée en fonction du type de boîte à outils que *nType* spécifie. Pour modifier les paramètres d’un ou de plusieurs types d’outils, appelez [CTooltipManager::SetTooltipParams](#settooltipparams).

Les types valides de pointe d’outils sont énumérés dans le tableau suivant :

|Type Tooltip|Catégorie de contrôle|Exemples types|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Un bouton.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Un bar de légende.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Tout contrôle qui ne correspond pas à une autre catégorie.|Aucun.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Une vitre amarable.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Zone de texte.|Aucun.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Un miniframe.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Un planificateur.|Aucun.|
|AFX_TOOLTIP_TYPE_RIBBON|Une barre de ruban.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Un contrôle de l’onglet.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Une barre d’outils.|CMFCToolBar, CMFCPopupMenuBar|
|AFX_TOOLTIP_TYPE_TOOLBOX|Une boîte à outils.|Aucun.|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a>CTooltipManager::DeleteToolTip

Supprime un contrôle d'info-bulle.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Paramètres

*pToolTip*<br/>
[dans, dehors] Une référence à un pointeur à un tooltip à détruire.

### <a name="remarks"></a>Notes

Appelez cette méthode pour chaque [classe CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) qui a été créé par [CTooltipManager::CreateToolTip](#createtooltip). Le contrôle parent doit appeler `OnDestroy` cette méthode de son gestionnaire. Ceci est nécessaire pour supprimer correctement le bout d’outil du cadre. Cette méthode définit *pToolTip* à NULL avant qu’il ne revienne.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a>CTooltipManager::SetTooltipParams

Personnalise l’apparence du contrôle de l’outil pour les types de contrôle Windows spécifiés.

```
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Paramètres

*nTypes*<br/>
[dans] Spécifie les types de contrôle.

*Cfrp*<br/>
[dans] Classe de temps d’exécution de l’outil personnalisé.

*pParams pParams*<br/>
[dans] Paramètres de l’outil.

### <a name="remarks"></a>Notes

Cette méthode définit la classe de temps d’exécution et les paramètres initiaux que le [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utilise lorsqu’il crée des outils. Lorsqu’un contrôle appelle [CTooltipManager::CreateToolTip](#createtooltip) et passe dans un type de boîte à outils qui est l’un des types indiqués par *nTypes*, le gestionnaire de pointe d’outils crée un contrôle de pointe d’outil qui est une instance de la classe de temps d’exécution spécifiée par *pRTC* et passe les paramètres spécifiés par *pParams* au nouveau tooltip.

Lorsque vous appelez cette méthode, tous les propriétaires de boîte à outils existantes reçoivent le message AFX_WM_UPDATETOOLTIPS et ils doivent recréer leurs outils en utilisant [CTooltipManager:CreateToolTip](#createtooltip).

*nTypes* peut être n’importe quelle combinaison des types valides de bout d’outils que [CTooltipManager: :CreateToolTip](#createtooltip) utilise, ou il peut être AFX_TOOLTIP_TYPE_ALL. Si vous passez AFX_TOOLTIP_TYPE_ALL, tous les types de bout d’outils sont affectés.

### <a name="example"></a>Exemple

L’exemple suivant montre comment `SetTooltipParams` utiliser `CTooltipManager` la méthode de la classe. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a>CTooltipManager::SetTooltipText

Définit le texte et la description d’un tooltip.

```
static void SetTooltipText(
    TOOLINFO* pTI,
    CToolTipCtrl* pToolTip,
    UINT nType,
    const CString strText,
    LPCTSTR lpszDescr=NULL);
```

### <a name="parameters"></a>Paramètres

*Pti*<br/>
[dans] Un pointeur vers un objet TOOLINFO.

*pToolTip*<br/>
[dans, dehors] Un pointeur vers le contrôle de l’outil pour lequel définir le texte et la description.

*nType*<br/>
[dans] Spécifie le type de contrôle auquel cette boîte à outils est associée.

*strText (en)*<br/>
[dans] Le texte à définir comme le texte de l’outiltip.

*lpszDescr*<br/>
[dans] Un pointeur à la description de l’outiltip. Sa valeur peut être NULL.

### <a name="remarks"></a>Notes

La valeur de *nType* doit être la même valeur que le paramètre *nType* de [CTooltipManager::CreateToolTip](#createtooltip) lorsque vous avez créé l’outiltip.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a>CTooltipManager::UpdateTooltips

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
void UpdateTooltips();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[Classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)
