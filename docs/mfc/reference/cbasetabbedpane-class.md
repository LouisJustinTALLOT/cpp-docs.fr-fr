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
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418866"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane, classe

Étend les fonctionnalités de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) pour prendre en charge la création de fenêtres à onglet.

## <a name="syntax"></a>Syntaxe

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Constructeur par défaut.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CBaseTabbedPane :: AddTab](#addtab)|Ajoute un nouvel onglet à un volet à onglets.|
|[CBaseTabbedPane :: AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Spécifie si un volet à onglets vide peut être détruit.|
|[CBaseTabbedPane :: ApplyRestoredTabInfo](#applyrestoredtabinfo)|Applique les paramètres de tabulation, qui sont chargés à partir du Registre, à un volet à onglets.|
|[CBaseTabbedPane :: CanFloat](#canfloat)|Détermine si le volet peut flotter. (Substitue [CBasePane :: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane :: CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Détermine si la légende du volet à onglets doit afficher le même texte que l’onglet actif.|
|[CBaseTabbedPane :: ConvertToTabbedDocument](#converttotabbeddocument)|(Substitue [CDockablePane :: ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane ::D etachPane](#detachpane)|Convertit un ou plusieurs volets ancrables en documents avec onglet MDI.|
|[CBaseTabbedPane :: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Active ou désactive la capacité du volet à onglets à synchroniser le texte de légende avec le texte d’étiquette de l’onglet actif.|
|[CBaseTabbedPane :: FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaure l’ordre de tabulation interne à un État par défaut.|
|[CBaseTabbedPane :: FindBarByTabNumber](#findbarbytabnumber)|Retourne un volet qui se trouve dans un onglet lorsque l’onglet est identifié par un index de base zéro.|
|||
|[CBaseTabbedPane :: FindPaneByID](#findpanebyid)|Retourne un volet identifié par l’ID du volet.|
|[CBaseTabbedPane :: FloatTab](#floattab)|Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable.|
|[CBaseTabbedPane :: GetDefaultTabsOrder](#getdefaulttabsorder)|Retourne l’ordre par défaut des onglets dans le volet.|
|[CBaseTabbedPane :: GetFirstVisibleTab](#getfirstvisibletab)|Récupère un pointeur vers le premier onglet affiché.|
|[CBaseTabbedPane :: GetMinSize](#getminsize)|Récupère la taille minimale autorisée pour le volet. (Substitue [CPane :: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane :: GetPaneIcon](#getpaneicon)|Retourne un handle vers l’icône du volet. (Substitue [CBasePane :: GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane :: GetPaneList](#getpanelist)|Retourne une liste de volets contenus dans le volet à onglets.|
|[CBaseTabbedPane :: GetTabArea](#gettabarea)|Retourne les rectangles englobants pour les zones d’onglets supérieure et inférieure.|
|[CBaseTabbedPane :: GetTabsNum](#gettabsnum)|Retourne le nombre d’onglets dans une fenêtre d’onglets.|
|[CBaseTabbedPane :: GetUnderlyingWindow](#getunderlyingwindow)|Obtient la fenêtre d’onglets (encapsulée) sous-jacente.|
|[CBaseTabbedPane :: GetVisibleTabsNum](#getvisibletabsnum)|Retourne le nombre d’onglets affichés.|
|[CBaseTabbedPane :: HasAutoHideMode](#hasautohidemode)|Détermine si le volet à onglets peut être basculé en mode de masquage automatique.|
|[CBaseTabbedPane :: IsHideSingleTab](#ishidesingletab)|Détermine si le volet à onglets est masqué si un seul onglet est affiché.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Utilisé en interne pendant la sérialisation.|
|[CBaseTabbedPane :: RecalcLayout](#recalclayout)|Recalcule les informations de disposition du volet. (Substitue [CPane :: RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane :: RemovePane](#removepane)|Supprime un volet du volet à onglets.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Utilisé en interne pendant la sérialisation.|
|`CBaseTabbedPane::Serialize`|(Substitue [CDockablePane :: Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Utilisé en interne pendant la sérialisation.|
|[CBaseTabbedPane :: SetAutoDestroy](#setautodestroy)|Détermine si la barre de contrôle à onglets est détruite automatiquement.|
|[CBaseTabbedPane :: SetAutoHideMode](#setautohidemode)|Bascule le volet d’ancrage entre le mode affiché et le mode de masquage automatique. (Substitue [CDockablePane :: SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane :: ShowTab](#showtab)|Affiche ou masque un onglet.|

## <a name="remarks"></a>Notes

Cette classe est une classe abstraite qui ne peut pas être instanciée. Il implémente les services qui sont communs à tous les types de volets à onglets.

Actuellement, la bibliothèque comprend deux classes de volet à onglets dérivées : la [classe CTabbedPane](../../mfc/reference/ctabbedpane-class.md) et la [classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

Un objet `CBaseTabbedPane` encapsule un pointeur vers un objet de [classe CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) . La [classe CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) devient alors une fenêtre enfant du volet à onglets.

Pour plus d’informations sur la création de volets à onglets, consultez classe [CDockablePane](../../mfc/reference/cdockablepane-class.md), classe [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)et [classe CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Spécifications

**En-tête :** afxBaseTabbedPane. h

##  <a name="addtab"></a>CBaseTabbedPane :: AddTab

Ajoute un nouvel onglet à un volet à onglets.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Paramètres

*pNewBar*<br/>
[in, out] Pointeur vers le volet à ajouter. Ce pointeur peut devenir non valide après l’appel de cette méthode. Pour plus d'informations, consultez la section Notes.

*bVisible*<br/>
dans TRUE pour rendre l’onglet visible ; Sinon, FALSe.

*bSetActive*<br/>
dans TRUE pour rendre l’onglet actif. Sinon, FALSe.

*bDetachable*<br/>
dans TRUE pour rendre l’onglet amovible ; Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été ajouté avec succès comme onglet et n’a pas été détruit dans le processus. FALSe si le volet ajouté est un objet de type `CBaseTabbedPane`. Pour plus d'informations, consultez la section Notes.

### <a name="remarks"></a>Notes

Appelez cette méthode pour ajouter un volet sous la forme d’un nouvel onglet sur un volet à onglets. Si *pNewBar* pointe vers un objet de type `CBaseTabbedPane`, tous ses onglets sont copiés dans le volet à onglets, puis *pNewBar* est détruit. Par conséquent, *pNewBar* devient un pointeur non valide et ne doit pas être utilisé.

##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane :: AllowDestroyEmptyTabbedPane

Spécifie si un volet à onglets vide peut être détruit.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si un volet à onglets vide peut être détruit ; Sinon, FALSe. L’implémentation par défaut retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Si un volet à onglets vide n’est pas autorisé à être détruit, le Framework masque à la place le volet.

##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane :: ApplyRestoredTabInfo

Charge les paramètres de tabulation à partir du Registre et les applique à un volet à onglets.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Paramètres

*bUseTabIndexes*<br/>
dans Ce paramètre est utilisé en interne par le Framework.

### <a name="remarks"></a>Notes

Cette méthode est appelée par l’infrastructure quand elle recharge les informations d’état d’ancrage à partir du Registre. La méthode obtient des informations sur l’ordre des tabulations et les noms des onglets pour un volet à onglets.

##  <a name="canfloat"></a>CBaseTabbedPane :: CanFloat

Spécifie si le volet à onglets peut flotter.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet peut flotter ; Sinon, FALSe.

##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane :: CanSetCaptionTextToTabName

Détermine si la légende du volet à onglets doit afficher le même texte que l’onglet actif.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le texte de légende du volet à onglets est défini sur le texte de l’onglet actif ; Sinon, FALSe.

### <a name="remarks"></a>Notes

La méthode est utilisée pour déterminer si le texte affiché dans la légende du volet à onglets duplique l’étiquette de l’onglet actif. Vous pouvez activer ou désactiver cette fonctionnalité en appelant [CBaseTabbedPane :: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

##  <a name="converttotabbeddocument"></a>CBaseTabbedPane :: ConvertToTabbedDocument

Convertit un ou plusieurs volets ancrables en documents avec onglet MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Paramètres

*bActiveTabOnly*<br/>
dans Lorsque vous convertissez un volet à onglets, spécifiez TRUE pour convertir uniquement l’onglet actif. spécifiez FALSe pour convertir tous les onglets dans le volet.

##  <a name="detachpane"></a>CBaseTabbedPane ::D etachPane

Détache un volet du volet à onglets.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
dans Pointeur vers le volet à détacher.

*bHide*<br/>
dans Paramètre booléen qui spécifie si l’infrastructure masque le volet après son détachement.

### <a name="return-value"></a>Valeur de retour

TRUE si le Framework détache correctement le volet ; FALSe si *pBar* a la valeur null ou s’il fait référence à un volet qui ne se trouve pas dans le volet à onglets.

### <a name="remarks"></a>Notes

Le Framework flotte le volet détaché si possible. Pour plus d’informations, consultez [CBasePane :: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane :: EnableSetCaptionTextToTabName

Active ou désactive la capacité du volet à onglets à synchroniser le texte de légende avec le texte d’étiquette de l’onglet actif.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans TRUE pour synchroniser la légende du volet à onglets avec la légende active de l’onglet. Sinon, FALSe.

##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane :: FillDefaultTabsOrderArray

Restaure l’ordre de tabulation interne à un État par défaut.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Notes

Cette méthode est appelée lorsque le Framework restaure l’état initial d’une barre Outlook.

##  <a name="findpanebyid"></a>CBaseTabbedPane :: FindPaneByID

Retourne un volet identifié par l’ID du volet.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Paramètres

*uBarID*<br/>
dans Spécifie l’ID du volet à rechercher.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le volet s’il a été trouvé ; Sinon, NULL.

### <a name="remarks"></a>Notes

Cette méthode compare tous les onglets du volet et retourne celui avec l’ID spécifié par le paramètre *uBarID* .

##  <a name="findbarbytabnumber"></a>CBaseTabbedPane :: FindBarByTabNumber

Retourne un volet qui se trouve dans un onglet.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Paramètres

*nTabNum*<br/>
dans Spécifie l’index de base zéro de l’onglet à récupérer.

*bGetWrappedBar*<br/>
dans TRUE pour retourner la fenêtre (encapsulée) sous-jacente du volet à la place du volet lui-même ; Sinon, FALSe. Cela s’applique uniquement aux volets dérivés de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Valeur de retour

Si le volet est trouvé, un pointeur valide vers le volet recherché est retourné ; Sinon, NULL.

### <a name="remarks"></a>Notes

Appelez cette méthode pour récupérer le volet résidant dans l’onglet spécifié par le paramètre *nTabNum* .

##  <a name="floattab"></a>CBaseTabbedPane :: FloatTab

Fait flotter un volet, mais seulement si le volet réside actuellement dans un onglet détachable.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in, out] Pointeur vers le volet à flotter.

*nTabID*<br/>
dans Spécifie l’index de base zéro de l’onglet à détacher.

*dockMethod*<br/>
dans Spécifie la méthode à utiliser pour rendre le volet flottant. Pour plus d'informations, consultez la section Notes.

*bHide*<br/>
dans TRUE pour masquer le volet avant qu’il ne soit flottant ; Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet est dissocié ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette méthode pour flotter un volet qui réside actuellement dans un onglet détachable.

Si vous souhaitez détacher un volet par programme, spécifiez DM_SHOW pour le paramètre *dockMethod* . Si vous souhaitez faire flotter le volet à la même position que celle qu’il a flotter précédemment, spécifiez DM_DBL_CLICK comme paramètre *dockMethod* .

##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane :: GetDefaultTabsOrder

Retourne l’ordre par défaut des onglets dans le volet.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Valeur de retour

Objet `CArray` qui spécifie l’ordre par défaut des onglets dans le volet.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode quand une barre Outlook est réinitialisée à un état initial.

##  <a name="getfirstvisibletab"></a>CBaseTabbedPane :: GetFirstVisibleTab

Récupère un pointeur vers le premier onglet affiché.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Paramètres

*iTabNum*<br/>
dans Référence à un entier. Cette méthode écrit l’index de base zéro du premier onglet affiché dans ce paramètre, ou-1 si aucun onglet affiché n’est trouvé.

### <a name="return-value"></a>Valeur de retour

En cas de réussite, pointeur vers le premier onglet affiché ; Sinon, NULL.

##  <a name="getminsize"></a>CBaseTabbedPane :: GetMinSize

Récupère la taille minimale autorisée pour le volet.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*size*<br/>
à Objet `CSize` rempli avec la taille minimale autorisée.

### <a name="remarks"></a>Notes

Si la gestion cohérente des tailles de volet minimales est active ( [CPane :: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), la *taille* est remplie avec la taille minimale autorisée pour l’onglet actif. sinon, la *taille* est remplie avec la valeur de retour de [CPane :: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpaneicon"></a>CBaseTabbedPane :: GetPaneIcon

Récupère la taille minimale autorisée pour le volet.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Paramètres

*size*<br/>
à Objet `CSize` rempli avec la taille minimale autorisée.

### <a name="remarks"></a>Notes

Si la gestion cohérente des tailles de volet minimales est active ( [CPane :: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), la *taille* est remplie avec la taille minimale autorisée pour l’onglet actif. sinon, la *taille* est remplie avec la valeur de retour de [CPane :: GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpanelist"></a>CBaseTabbedPane :: GetPaneList

Retourne une liste de volets contenus dans le volet à onglets.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Paramètres

*LST*<br/>
à `CObList` rempli avec les volets contenus dans le volet à onglets.

*pRTCFilter*<br/>
dans Si la valeur n’est pas NULL, la liste retournée contient uniquement les volets qui appartiennent à la classe d’exécution spécifiée.

##  <a name="gettabarea"></a>CBaseTabbedPane :: GetTabArea

Retourne les rectangles englobants pour les zones d’onglets supérieure et inférieure.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Paramètres

*rectTabAreaTop*<br/>
à Reçoit les coordonnées d’écran de la zone d’onglet supérieure.

*rectTabAreaBottom*<br/>
à Reçoit les coordonnées d’écran de la zone d’onglet inférieure.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer les rectangles englobants, en coordonnées d’écran, pour les zones d’onglets supérieure et inférieure.

##  <a name="gettabsnum"></a>CBaseTabbedPane :: GetTabsNum

Retourne le nombre d’onglets dans une fenêtre d’onglets.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’onglets dans le volet à onglets.

##  <a name="getunderlyingwindow"></a>CBaseTabbedPane :: GetUnderlyingWindow

Obtient la fenêtre d’onglets (encapsulée) sous-jacente.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre d’onglet sous-jacente.

##  <a name="getvisibletabsnum"></a>CBaseTabbedPane :: GetVisibleTabsNum

Retourne le nombre d’onglets visibles.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre d’onglets visibles, qui seront supérieurs ou égaux à zéro.

### <a name="remarks"></a>Notes

Appelez cette méthode pour déterminer le nombre d’onglets visibles dans le volet à onglets.

##  <a name="hasautohidemode"></a>CBaseTabbedPane :: HasAutoHideMode

Détermine si le volet à onglets peut passer en mode masquage automatique.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le volet peut être basculé en mode de masquage automatique ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si le mode de masquage automatique est désactivé, aucun bouton pin n’est affiché dans la légende du volet à onglets.

##  <a name="ishidesingletab"></a>CBaseTabbedPane :: IsHideSingleTab

Détermine si le volet à onglets est masqué si un seul onglet est affiché.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si la fenêtre d’onglet n’est pas affichée lorsqu’il n’y a qu’un seul onglet visible ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Si le volet n’est pas affiché parce qu’un seul onglet est ouvert, vous pouvez appeler cette méthode pour déterminer si le volet à onglets fonctionne correctement.

##  <a name="removepane"></a>CBaseTabbedPane :: RemovePane

Supprime un volet du volet à onglets.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
[in, out] Pointeur vers le volet à supprimer du volet à onglets.

### <a name="return-value"></a>Valeur de retour

TRUE si le volet a été correctement supprimé du volet à onglets et si le volet à onglets est toujours valide. FALSe si le dernier volet a été supprimé du volet à onglets et que le volet à onglets va être détruit. Si la valeur de retour est FALSe, n’utilisez plus le volet à onglets.

### <a name="remarks"></a>Notes

Appelez cette méthode pour supprimer le volet spécifié par le paramètre *pBar* du volet à onglets.

##  <a name="setautodestroy"></a>CBaseTabbedPane :: SetAutoDestroy

Détermine si la barre de contrôle à onglets est détruite automatiquement.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Paramètres

*bAutoDestroy*<br/>
dans TRUE si le volet à onglets a été créé dynamiquement et que vous ne contrôlez pas sa durée de vie. Sinon, FALSe.

### <a name="remarks"></a>Notes

Définissez le mode de destruction automatique sur TRUE si vous créez un volet à onglets de manière dynamique et si vous ne contrôlez pas sa durée de vie. Si le mode de destruction automatique a la valeur TRUE, le volet à onglets est détruit automatiquement par l’infrastructure.

##  <a name="showtab"></a>CBaseTabbedPane :: ShowTab

Affiche ou masque un onglet.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*pBar*<br/>
dans Pointeur vers le volet à afficher ou masquer.

*bShow*<br/>
dans TRUE pour afficher le volet ; FALSe pour masquer le volet.

*bDelay*<br/>
dans TRUE pour différer l’ajustement de la disposition des onglets ; Sinon, FALSe.

*bActivate*<br/>
dans TRUE pour rendre l’onglet actif. Sinon, FALSe.

### <a name="return-value"></a>Valeur de retour

TRUE si l’onglet a été affiché ou masqué avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Lorsque vous appelez cette méthode, un volet est affiché ou masqué, selon la valeur du paramètre *bShow* . Si vous masquez un onglet et qu’il s’agit du dernier onglet visible dans la fenêtre sous-jacente, le volet à onglets est masqué. Si vous affichez un onglet alors qu’il n’y avait précédemment aucun onglet visible, le volet à onglets s’affiche.

##  <a name="recalclayout"></a>CBaseTabbedPane :: RecalcLayout

Recalcule les informations de disposition du volet.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Notes

Si le volet est flottant, cette méthode indique au Framework de redimensionner le volet à la taille actuelle du mini-frame.

Si le volet est ancré, cette méthode n’a aucun effet.

##  <a name="setautohidemode"></a>CBaseTabbedPane :: SetAutoHideMode

Définit le mode de masquage automatique pour les volets détachables dans le volet à onglets.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Paramètres

*bMode*<br/>
dans TRUE pour activer le mode de masquage automatique ; FALSe pour activer le mode d’ancrage normal.

*dwAlignment*<br/>
dans Spécifie l’alignement du volet à masquage automatique à créer. Pour obtenir la liste des valeurs possibles, consultez [CPane :: MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[in, out] Pointeur vers la barre d’outils de masquage automatique en cours. Sa valeur peut être NULL.

*bUseTimer*<br/>
dans Spécifie s’il faut utiliser l’effet de masquage automatique lorsque l’utilisateur bascule le volet en mode de masquage automatique, ou pour masquer immédiatement le volet.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la barre d’outils de masquage automatique qui est créée lors du basculement en mode de masquage automatique, ou NULL si aucune barre d’outils n’est créée.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode quand un utilisateur clique sur le bouton épingler pour basculer le volet à onglets pour qu’il soit en mode de masquage automatique ou en mode d’ancrage normal.

Le mode de masquage automatique est défini pour chaque volet détachable dans le volet à onglets. Les volets qui ne sont pas détachables sont ignorés. Pour plus d’informations, consultez [CMFCBaseTabCtrl :: EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Appelez cette méthode pour faire basculer un volet à onglets pour masquer automatiquement le mode par programme. Le volet doit être ancré à la fenêtre frame principale ( [CDockablePane :: GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) doit retourner un pointeur valide vers [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane Class](../../mfc/reference/cdockablepane-class.md)
