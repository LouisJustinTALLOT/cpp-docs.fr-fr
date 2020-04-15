---
title: CBaseTabbedPane, classe
ms.date: 11/04/2016
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
ms.openlocfilehash: ce7c48263ed511545757c94d61552e6206e74a00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352855"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane, classe

Étend les fonctionnalités de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) pour prendre en charge la création de fenêtres à onglet.

## <a name="syntax"></a>Syntaxe

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Ajoute un nouvel onglet à une vitre tabbed.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Précise si une vitre vide peut être détruite.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Applique les paramètres de l’onglet, qui sont chargés à partir du registre, à une vitre tabbed.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Détermine si la vitre peut flotter. (Overrides [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Détermine si la légende de la vitre ongletnée doit afficher le même texte que l’onglet actif.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Overrides [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Convertit une ou plusieurs vitres amarables en documents tabbed MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Permet ou désactive la capacité de la vitre tabbed de synchroniser le texte de légende avec le texte d’étiquette sur l’onglet actif.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaure l’ordre d’onglet interne à un état par défaut.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Retourne une vitre qui réside dans un onglet lorsque l’onglet est identifié par un index d’onglet à base nulle.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Retourne une vitre identifiée par l’ID de la vitre.|
|[CBaseTabbedPane::FloatTab](#floattab)|Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Retourne l’ordre par défaut des onglets dans la vitre.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Récupère un pointeur sur le premier onglet affiché.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Récupère la taille minimale autorisée pour la vitre. (Overrides [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Retourne une poignée à l’icône de la vitre. (Overrides [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Retourne une liste de vitres contenues dans la vitre.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Retourne les rectangles de délimitation pour les zones d’onglet supérieur et inférieur.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Retourne le nombre d’onglets dans une fenêtre d’onglet.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Obtient la fenêtre sous-jacente (enveloppée) d’onglet.|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Retourne le nombre d’onglets affichés.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Détermine si la vitre tabbed peut être commutée en mode auto-cacher.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Détermine si la vitre tabbed est cachée si un seul onglet est affiché.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Utilisé en interne lors de la sérialisation.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Recalcule les informations de mise en page pour la vitre. (Overrides [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Retire une vitre de la vitre.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Utilisé en interne lors de la sérialisation.|
|`CBaseTabbedPane::Serialize`|(Overrides [CDockablePane::Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Utilisé en interne lors de la sérialisation.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Détermine si la barre de commande tabbed sera détruite automatiquement.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Bascule la vitre d’amarrage entre le mode affiché et le mode auto-cacher. (Overrides [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::ShowTab](#showtab)|Affiche ou cache un onglet.|

## <a name="remarks"></a>Notes

Cette classe est une classe abstraite et ne peut pas être instantanée. Il met en œuvre les services qui sont communs à toutes sortes de vitres tabbed.

Actuellement, la bibliothèque comprend deux classes dérivées de volets tabbed: [classe CTabbedPane](../../mfc/reference/ctabbedpane-class.md) et [CMFCOutlookBar Classe](../../mfc/reference/cmfcoutlookbar-class.md).

Un `CBaseTabbedPane` objet enveloppe un pointeur vers un objet [cmFCBaseTabCtrl Class.](../../mfc/reference/cmfcbasetabctrl-class.md) [CMFCBaseTabCtrl Classe](../../mfc/reference/cmfcbasetabctrl-class.md) devient alors une fenêtre d’enfant de la vitre tabbed.

Pour plus d’informations sur la façon de créer des vitres tabbed, voir [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md), et [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Spécifications

**En-tête:** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbedPane::AddTab

Ajoute un nouvel onglet à une vitre tabbed.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Paramètres

*pNewBar (en)*<br/>
[dans, dehors] Un pointeur à la vitre à ajouter. Ce pointeur peut devenir invalide après que vous avez appelé cette méthode. Pour plus d'informations, consultez la section Notes.

*bVisible*<br/>
[dans] VRAI pour rendre l’onglet visible; autrement, FALSE.

*bSetActive (en anglais)*<br/>
[dans] VRAI pour faire de l’onglet l’onglet actif; autrement, FALSE.

*bDétachable*<br/>
[dans] VRAI pour rendre l’onglet amovible; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

VRAI si le volet a été ajouté avec succès comme un onglet et n’a pas été détruit dans le processus. FALSE si le volet ajouté est `CBaseTabbedPane`un objet de type . Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajouter une vitre comme nouvel onglet sur une vitre tabbed. Si *pNewBar* pointe vers `CBaseTabbedPane`un objet de type, tous ses onglets sont copiés sur la vitre tabbed, puis *pNewBar* est détruit. Ainsi, *pNewBar* devient un pointeur invalide et ne doit pas être utilisé.

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Précise si une vitre vide peut être détruite.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si une vitre tabbed vide peut être détruite; autrement, FALSE. L’implémentation par défaut renvoie toujours TRUE.

### <a name="remarks"></a>Notes

Si une vitre tabbed vide n’est pas autorisée à être détruite, le cadre cache la vitre à la place.

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Charge les paramètres de l’onglet du registre et les applique à une vitre tabbed.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Paramètres

*bUseTabIndexes*<br/>
[dans] Ce paramètre est utilisé en interne par le cadre.

### <a name="remarks"></a>Notes

Cette méthode est appelée par le cadre lorsqu’elle recharge les informations d’état d’amarrage du registre. La méthode obtient des informations sur l’ordre de l’onglet et les noms d’onglets pour une vitre tabbed.

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbedPane::CanFloat

Précise si la vitre tabbed peut flotter.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre peut flotter; autrement, FALSE.

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Détermine si la légende de la vitre ongletnée doit afficher le même texte que l’onglet actif.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le texte de légende de la vitre tabbed est réglé sur le texte de l’onglet actif; autrement, FALSE.

### <a name="remarks"></a>Notes

La méthode est utilisée pour déterminer si le texte affiché sur la légende de la vitre tabbed reproduit l’étiquette de l’onglet actif. Vous pouvez activer ou désactiver cette fonctionnalité en appelant [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Convertit une ou plusieurs vitres amarables en documents tabbed MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bActiveTabOnly*<br/>
[dans] Lorsque vous convertissez une vitre tabbed, spécifiez VRAI pour convertir uniquement l’onglet actif. Spécifiez FALSE pour convertir tous les onglets dans la vitre.

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::DetachPane

Détache une vitre de la vitre tabbed.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans] Pointeur sur la vitre pour se détacher.

*bHide (en)*<br/>
[dans] Paramètre Boolean qui précise si le cadre cache la vitre après qu’il soit détaché.

### <a name="return-value"></a>Valeur de retour

VRAI si le cadre détache avec succès la vitre; FALSE si *pBar* est NULL ou se réfère à un volet qui n’est pas dans la vitre tabbed.

### <a name="remarks"></a>Notes

Le cadre flotte la vitre détachée si possible. Pour plus d’informations, voir [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Permet ou désactive la capacité de la vitre tabbed de synchroniser le texte de légende avec le texte d’étiquette sur l’onglet actif.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] VRAI pour synchroniser la légende de la vitre avec la légende de l’onglet actif; autrement, FALSE.

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Restaure l’ordre d’onglet interne à un état par défaut.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée lorsque le cadre rétablit une barre Outlook à un état initial.

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Renvoie une vitre identifiée par l’ID de la vitre.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Paramètres

*uBarID (en)*<br/>
[dans] Spécifie l’ID de la vitre à trouver.

### <a name="return-value"></a>Valeur de retour

Un pointeur à la vitre si elle a été trouvée; autrement, NULL.

### <a name="remarks"></a>Notes

Cette méthode compare tous les onglets dans la vitre et renvoie celui avec l’ID spécifié par le paramètre *uBarID.*

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Retourne une vitre qui réside dans un onglet.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Paramètres

*nTabNum (en)*<br/>
[dans] Spécifie l’index zéro de l’onglet à récupérer.

*bGetWrappedBar (en anglais seulement)*<br/>
[dans] VRAI pour retourner la fenêtre sous-jacente (enveloppée) de la vitre au lieu de la vitre elle-même; autrement FALSE. Cela ne s’applique qu’aux vitres dérivées de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Valeur de retour

Si la vitre est trouvée, alors un pointeur valide à la vitre recherchée est retourné; autrement, NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le volet résidant dans l’onglet spécifié par le paramètre *nTabNum.*

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbedPane::FloatTab

Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans, dehors] Un pointeur à la vitre pour flotter.

*nTabID (en)*<br/>
[dans] Spécifie l’indice zéro de l’onglet à flotter.

*dockMethod*<br/>
[dans] Spécifie la méthode à utiliser pour faire flotter la vitre. Pour plus d'informations, consultez la section Notes.

*bHide (en)*<br/>
[dans] VRAI pour cacher la vitre avant de flotter; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre flottait; autrement, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour faire flotter une vitre qui réside actuellement dans un onglet amovible.

Si vous souhaitez détacher un volet de manière programmatique, spécifiez DM_SHOW pour le paramètre *dockMethod.* Si vous voulez faire flotter la vitre dans la même position où elle flottait auparavant, spécifiez DM_DBL_CLICK comme *paramètre dockMethod.*

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Retourne l’ordre par défaut des onglets dans la vitre.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Valeur de retour

Un `CArray` objet qui spécifie l’ordre par défaut des onglets dans la vitre.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’une barre Outlook est réinitialisée à un état initial.

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Récupère un pointeur sur le premier onglet affiché.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Paramètres

*iTabNum (en)*<br/>
[dans] Une référence à un intégrant. Cette méthode écrit l’index à base zéro de la première onglet affichée à ce paramètre, ou -1 si aucun onglet affiché n’est trouvé.

### <a name="return-value"></a>Valeur de retour

En cas de succès, un pointeur sur le premier onglet affiché; autrement, NULL.

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbedPane::GetMinSize

Récupère la taille minimale autorisée pour la vitre.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
[out] Un `CSize` objet qui est rempli de la taille minimale autorisée.

### <a name="remarks"></a>Notes

Si une manipulation cohérente des tailles minimales de vitres est active ( [CPane: ::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), la *taille* est remplie de la taille minimale autorisée pour l’onglet actif. Sinon, la *taille* est remplie de la valeur de retour de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Récupère la taille minimale autorisée pour la vitre.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*Taille*<br/>
[out] Un `CSize` objet qui est rempli de la taille minimale autorisée.

### <a name="remarks"></a>Notes

Si une manipulation cohérente des tailles minimales de vitres est active ( [CPane: ::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), la *taille* est remplie de la taille minimale autorisée pour l’onglet actif. Sinon, la *taille* est remplie de la valeur de retour de [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbedPane::GetPaneList

Retourne une liste de vitres contenues dans la vitre.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Paramètres

*Lst*<br/>
[out] Un `CObList` qui est rempli avec les vitres qui sont contenues dans la vitre tabbed.

*pRTCFilter (en)*<br/>
[dans] S’il n’est pas NULL, la liste retournée ne contient que des volets qui sont de la classe de temps d’exécution spécifiée.

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Retourne les rectangles de délimitation pour les zones d’onglet supérieur et inférieur.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
[out] Reçoit les coordonnées de l’écran de la zone supérieure de l’onglet.

*rectTabAreaBottom*<br/>
[out] Reçoit les coordonnées de l’écran de la zone de l’onglet inférieur.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer les rectangles de délimitation, dans les coordonnées de l’écran, pour les zones d’onglet supérieure et inférieure.

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Retourne le nombre d’onglets dans une fenêtre d’onglet.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’onglets dans la vitre tabbed.

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Obtient la fenêtre sous-jacente (enveloppée) d’onglet.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la fenêtre d’onglet sous-jacente.

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Retourne le nombre d’onglets visibles.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’onglets visibles, qui sera supérieur ou égal à zéro.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer le nombre d’onglets visibles dans la vitre tabbed.

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Détermine si le volet à onglets peut passer en mode masquage automatique.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le volet peut être commuté en mode autohide; autrement, FALSE.

### <a name="remarks"></a>Notes

Si le mode autohide est désactivé, aucun bouton d’épingle n’est affiché sur la légende de la vitre tabbed.

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Détermine si la vitre tabbed est cachée si un seul onglet est affiché.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre de l’onglet n’est pas affichée lorsqu’il n’y a qu’un seul onglet visible; autrement, FALSE.

### <a name="remarks"></a>Notes

Si le volet n’est pas affiché parce qu’un seul onglet est ouvert, vous pouvez appeler cette méthode pour déterminer si la vitre tabbed fonctionne correctement.

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbedPane::RemovePane

Retire une vitre de la vitre.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans, dehors] Un pointeur à la vitre à retirer de la vitre tabbed.

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre a été enlevée avec succès de la vitre tabbed et si la vitre tabbed est toujours valide. FALSE si le dernier volet a été retiré de la vitre tabbed et la vitre tabbed est sur le point d’être détruite. Si la valeur de retour est FALSE, n’utilisez plus la vitre tabbed.

### <a name="remarks"></a>Notes

Appelez cette méthode pour enlever la vitre spécifiée par le paramètre *pBar* de la vitre tabbed.

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Détermine si la barre de commande tabbed sera détruite automatiquement.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
[dans] VRAI si la vitre tabbed a été créée dynamiquement et que vous ne contrôlez pas sa durée de vie; autrement, FALSE.

### <a name="remarks"></a>Notes

Définissez le mode auto-destruction à TRUE si vous créez un volet tabbed dynamiquement et si vous ne contrôlez pas sa durée de vie. Si le mode auto-destruction est VRAI, la vitre tabbed sera détruite automatiquement par le cadre.

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbedPane::ShowTab

Affiche ou cache un onglet.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*pBar (pBar)*<br/>
[dans] Un pointeur à la vitre pour montrer ou se cacher.

*bShow (en)*<br/>
[dans] VRAI pour montrer la vitre; FALSE pour cacher la vitre.

*bDelay (en)*<br/>
[dans] VRAI pour retarder l’ajustement de la disposition de l’onglet; autrement, FALSE.

*bActivate (en)*<br/>
[dans] VRAI pour faire de l’onglet l’onglet actif; autrement, FALSE.

### <a name="return-value"></a>Valeur de retour

VRAI si l’onglet a été montré ou caché avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Lorsque vous appelez cette méthode, un volet est soit affiché ou caché, selon la valeur du *paramètre bShow.* Si vous cachez un onglet et que c’est le dernier onglet visible dans la fenêtre de l’onglet sous-jacent, la vitre tabbed est cachée. Si vous affichez un onglet lorsqu’il n’y avait auparavant aucun onglet visible, la vitre tabbed est affichée.

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Recalcule les informations de mise en page pour la vitre.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

Si la vitre flotte, cette méthode informe le cadre pour redimensionner la vitre à la taille actuelle du mini-cadre.

Si la vitre est amarré, cette méthode ne fait rien.

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode

Définit le mode auto-cacher pour les vitres amovibles dans la vitre tabbed.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Paramètres

*bMode*<br/>
[dans] VRAI pour activer le mode auto-cacher; FALSE pour activer le mode d’amarrage régulier.

*dwAlignment*<br/>
[dans] Spécifie l’alignement de la vitre automatique qui doit être créée. Pour une liste de valeurs possibles, voir [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[dans, dehors] Un pointeur à la barre d’outils actuelle auto-cacher. Sa valeur peut être NULL.

*bUseTimer (en)*<br/>
[dans] Précise s’il faut utiliser l’effet de cache automatique lorsque l’utilisateur passe la vitre en mode auto-cacher, ou pour cacher la vitre immédiatement.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la barre d’outils de cache automatique qui est créé lors du passage au mode auto-cacher, ou NULL si aucune barre d’outils n’est créée.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’un utilisateur choisit le bouton d’épingle pour passer de la vitre tabbed en mode auto-cacher ou en mode d’amarrage régulier.

Le mode auto-cacher est réglé pour chaque volet amovible dans la vitre tabbed. Les vitres qui ne sont pas amovibles sont ignorées. Pour plus d’informations, voir [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Appelez cette méthode pour passer un volet tabbed en mode auto-cacher programmatiquement. La vitre doit être amarrée à la fenêtre du cadre principal ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) doit retourner un pointeur valide au [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane, classe](../../mfc/reference/cdockablepane-class.md)
