---
description: 'En savoir plus sur : classe CTooltipManager'
title: CTooltipManager, classe
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
ms.openlocfilehash: 0ec6d691abbceb7026fe9656c17ff899f1d07759
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318544"
---
# <a name="ctooltipmanager-class"></a>CTooltipManager, classe

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

Utilisez la [classe CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo` , et `CTooltipManager` ensemble pour implémenter des info-bulles personnalisées dans votre application. Pour obtenir un exemple d’utilisation de ces classes d’info-bulle, consultez la rubrique relative à la [classe CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxtooltipmanager. h

## <a name="ctooltipmanagercreatetooltip"></a><a name="createtooltip"></a> CTooltipManager :: CreateToolTip

Crée un contrôle ToolTip.

```
static BOOL CreateToolTip(
    CToolTipCtrl*& pToolTip,
    CWnd* pWndParent,
    UINT nType);
```

### <a name="parameters"></a>Paramètres

*pToolTip*<br/>
à Référence à un pointeur d’info-bulle. Elle est définie pour pointer vers l’info-bulle qui vient d’être créée lorsque la fonction retourne.

*pWndParent*<br/>
dans Parent de l’info-bulle.

*nType*<br/>
dans Type de l’info-bulle.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si une info-bulle a été créée avec succès.

### <a name="remarks"></a>Notes

Vous devez appeler [CTooltipManager ::D eletetooltip](#deletetooltip) pour supprimer le contrôle ToolTip qui est retourné dans *pToolTip*.

[CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) définit les paramètres d’affichage visuels de chaque info-bulle qu’il crée en fonction du type d’info-bulle que *ndéclarations* spécifie. Pour modifier les paramètres d’un ou de plusieurs types d’info-bulles, appelez [CTooltipManager :: SetTooltipParams](#settooltipparams).

Les types d’info-bulles valides sont répertoriés dans le tableau suivant :

|Type d’info-bulle|Catégorie de contrôle|Exemples de types|
|------------------|----------------------|-------------------|
|AFX_TOOLTIP_TYPE_BUTTON|Bouton.|CMFCButton|
|AFX_TOOLTIP_TYPE_CAPTIONBAR|Barre de légende.|CMFCCaptionBar|
|AFX_TOOLTIP_TYPE_DEFAULT|Tout contrôle qui ne correspond pas à une autre catégorie.|Aucun.|
|AFX_TOOLTIP_TYPE_DOCKBAR|Un volet Ancrable.|CDockablePane|
|AFX_TOOLTIP_TYPE_EDIT|Zone de texte.|Aucun.|
|AFX_TOOLTIP_TYPE_MINIFRAME|Miniframe.|CPaneFrameWnd|
|AFX_TOOLTIP_TYPE_PLANNER|Un planificateur.|Aucun.|
|AFX_TOOLTIP_TYPE_RIBBON|Barre de ruban.|CMFCRibbonBar, CMFCRibbonPanelMenuBar|
|AFX_TOOLTIP_TYPE_TAB|Contrôle onglet.|CMFCTabCtrl|
|AFX_TOOLTIP_TYPE_TOOLBAR|Une barre d’outils.|CMFCToolBar, Cmfcpopupmenubar,|
|AFX_TOOLTIP_TYPE_TOOLBOX|Boîte à outils.|Aucun.|

## <a name="ctooltipmanagerdeletetooltip"></a><a name="deletetooltip"></a> CTooltipManager ::D eleteToolTip

Supprime un contrôle d'info-bulle.

```
static void DeleteToolTip(CToolTipCtrl*& pToolTip);
```

### <a name="parameters"></a>Paramètres

*pToolTip*<br/>
[in, out] Référence à un pointeur vers une info-bulle à détruire.

### <a name="remarks"></a>Notes

Appelez cette méthode pour chaque [classe CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) créée par [CTooltipManager :: CreateToolTip](#createtooltip). Le contrôle parent doit appeler cette méthode à partir de son `OnDestroy` Gestionnaire. Cela est nécessaire pour supprimer correctement l’info-bulle du Framework. Cette méthode affecte la valeur NULL à *pToolTip* avant de retourner.

## <a name="ctooltipmanagersettooltipparams"></a><a name="settooltipparams"></a> CTooltipManager :: SetTooltipParams

Personnalise l’apparence du contrôle ToolTip pour les types de contrôles Windows spécifiés.

```cpp
void SetTooltipParams(
    UINT nTypes,
    CRuntimeClass* pRTC=RUNTIME_CLASS(CMFCToolTipCtrl),
    CMFCToolTipInfo* pParams=NULL);
```

### <a name="parameters"></a>Paramètres

*nTypes*<br/>
dans Spécifie les types de contrôle.

*pRTC*<br/>
dans Classe Runtime de l’info-bulle personnalisée.

*pParams*<br/>
dans Paramètres d’info-bulle.

### <a name="remarks"></a>Notes

Cette méthode définit la classe d’exécution et les paramètres initiaux que le [CToolTipManager](../../mfc/reference/ctooltipmanager-class.md) utilise lorsqu’il crée des info-bulles. Lorsqu’un contrôle appelle [CTooltipManager :: CreateToolTip](#createtooltip) et passe dans un type d’info-bulle qui est l’un des types indiqués par *nTypes*, le gestionnaire d’info-bulles crée un contrôle ToolTip qui est une instance de la classe Runtime spécifiée par *pRTC* et passe les paramètres spécifiés par *pParams* à la nouvelle info-bulle.

Lorsque vous appelez cette méthode, tous les propriétaires d’info-bulle existants reçoivent le message AFX_WM_UPDATETOOLTIPS et ils doivent recréer leurs info-bulles à l’aide de [CTooltipManager :: CreateToolTip](#createtooltip).

*nTypes* peut être n’importe quelle combinaison de types d’info-bulles valides que [CTooltipManager :: CreateToolTip](#createtooltip) utilise, ou il peut être AFX_TOOLTIP_TYPE_ALL. Si vous transmettez AFX_TOOLTIP_TYPE_ALL, tous les types d’info-bulle sont affectés.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser la `SetTooltipParams` méthode de la `CTooltipManager` classe. Cet extrait de code fait partie de l’ [exemple Draw Client](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#11](../../mfc/reference/codesnippet/cpp/ctooltipmanager-class_1.cpp)]

## <a name="ctooltipmanagersettooltiptext"></a><a name="settooltiptext"></a> CTooltipManager :: SetTooltipText

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

*pTI*<br/>
dans Pointeur vers un objet TOOLINFO.

*pToolTip*<br/>
[in, out] Pointeur vers le contrôle d’info-bulle pour lequel le texte et la description doivent être définis.

*nType*<br/>
dans Spécifie le type de contrôle auquel cette info-bulle est associée.

*strText*<br/>
dans Texte à définir comme texte d’info-bulle.

*lpszDescr*<br/>
dans Pointeur vers la description de l’info-bulle. Sa valeur peut être NULL.

### <a name="remarks"></a>Notes

La valeur de *ndéclarations* doit être identique à celle du paramètre *ndéclarations* de [CTooltipManager :: CreateToolTip](#createtooltip) lorsque vous avez créé l’info-bulle.

## <a name="ctooltipmanagerupdatetooltips"></a><a name="updatetooltips"></a> CTooltipManager :: UpdateTooltips

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```cpp
void UpdateTooltips();
```

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolTipCtrl, classe](../../mfc/reference/cmfctooltipctrl-class.md)<br/>
[CMFCToolTipInfo, classe](../../mfc/reference/cmfctooltipinfo-class.md)
