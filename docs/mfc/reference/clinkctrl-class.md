---
title: CLinkCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372257"
---
# <a name="clinkctrl-class"></a>CLinkCtrl, classe

Fournit les fonctionnalités du contrôle commun SysLink Windows.

## <a name="syntax"></a>Syntaxe

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Construit un objet `CLinkCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CLinkCtrl::Créer](#create)|Crée un contrôle de lien `CLinkCtrl` et l’attache à un objet.|
|[CLinkCtrl::CreateEx](#createex)|Crée un contrôle de lien avec des `CLinkCtrl` styles étendus et l’attache à un objet.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Récupère la hauteur idéale du contrôle du lien.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Calcule la hauteur préférée du texte de lien pour le contrôle de lien actuel, selon la largeur spécifiée du lien.|
|[CLinkCtrl::GetItem](#getitem)|Récupère les états et les attributs d’un élément de contrôle de lien.|
|[CLinkCtrl::GetItemID](#getitemid)|Récupère l’ID d’un élément de contrôle de lien.|
|[CLinkCtrl::GetItemState](#getitemstate)|Récupère l’état de l’élément de contrôle du lien.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Récupère l’URL représentée par l’élément de contrôle du lien.|
|[CLinkCtrl::HitTest](#hittest)|Détermine si l’utilisateur a cliqué sur le lien spécifié.|
|[CLinkCtrl::SetItem](#setitem)|Définit les états et les attributs d’un élément de contrôle de lien.|
|[CLinkCtrl::SetItemID](#setitemid)|Définit l’ID d’un élément de contrôle de lien.|
|[CLinkCtrl::SetItemState](#setitemstate)|Définit l’état de l’élément de contrôle du lien.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Définit l’URL représentée par l’élément de contrôle du lien.|

## <a name="remarks"></a>Notes

Un « contrôle de liaison » fournit un moyen pratique d’intégrer des liens hypertexte dans une fenêtre. Le contrôle réel est une fenêtre qui rend le texte balisé et lance des applications appropriées lorsque l’utilisateur clique sur un lien intégré. Plusieurs liens sont pris en charge dans un seul contrôle et peuvent être consultés par un index zéro.

Ce contrôle (et `CLinkCtrl` donc la classe) n’est disponible que pour les programmes fonctionnant sous Windows XP et plus tard.

Pour plus d’informations, voir [SysLink Control](/windows/win32/Controls/syslink-overview) dans windows SDK.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>CLinkCtrl::CLinkCtrl

Construit un objet `CLinkCtrl`.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>CLinkCtrl::Créer

Crée un contrôle de lien `CLinkCtrl` et l’attache à un objet.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Paramètres

*lpszLinkMarkup (en)*<br/>
Pointeur vers une chaîne à zéro fin qui contient le texte marqué vers le haut pour afficher. Pour plus d’informations, voir la section "Markup and Link Access" dans le sujet [Aperçu des contrôles SysLink](/windows/win32/Controls/syslink-overview).

*dwStyle (en)*<br/>
Spécifie le style du contrôle du lien. Appliquer n’importe quelle combinaison de styles de contrôle. Voir [Common Control](/windows/win32/Controls/common-control-styles) `Windows SDK` Styles pour plus d’informations.

*Rect*<br/>
Spécifie la taille et la position du contrôle du lien. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle du lien. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle du lien.

### <a name="return-value"></a>Valeur de retour

VRAI si l’initialisation a été couronnée de succès; autrement FALSE.

### <a name="remarks"></a>Notes

Vous construisez un `CLinkCtrl` objet en deux étapes. Tout d’abord, appelez `Create`le constructeur, puis appelez , ce `CLinkCtrl` qui crée le contrôle de lien et le fixe à l’objet. Si vous souhaitez utiliser des styles windows étendus avec votre contrôle, `Create`appelez [CLinkCtrl::CreateEx](#createex) au lieu de .

La deuxième forme `Create` de la méthode est dépréciée. Utilisez le premier formulaire qui spécifie le paramètre *lpszLinkMarkup.*

### <a name="example"></a>Exemple

L’exemple de code suivant `m_Link1` définit `m_Link2`deux variables, nommées et , qui sont utilisées pour accéder à deux contrôles de liaison.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant crée un contrôle de lien basé sur l’emplacement d’un autre contrôle de lien. Le chargeur de ressources crée le premier contrôle de lien lorsque votre application démarre. Lorsque votre application entre dans la méthode OnInitDialog, vous créez le deuxième contrôle de lien par rapport à la position du contrôle du premier lien. Ensuite, vous resize le deuxième contrôle de lien pour s’adapter au texte qu’il affiche.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>CLinkCtrl::CreateEx

Crée un contrôle de lien avec des `CLinkCtrl` styles étendus et l’attache à un objet.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Paramètres

*lpszLinkMarkup (en)*<br/>
Pointeur vers une chaîne à zéro fin qui contient le texte marqué vers le haut pour afficher. Pour plus d’informations, voir la section "Markup and Link Access" dans le sujet [Aperçu des contrôles SysLink](/windows/win32/Controls/syslink-overview).

*dwExStyle (en anglais)*<br/>
Spécifie le style étendu du contrôle du lien. Pour une liste de styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le Windows SDK.

*dwStyle (en)*<br/>
Spécifie le style du contrôle du lien. Appliquer n’importe quelle combinaison de styles de contrôle. Pour plus d’informations, voir [Styles de contrôle commun](/windows/win32/Controls/common-control-styles) dans le SDK Windows.

*Rect*<br/>
Spécifie la taille et la position du contrôle du lien. Il peut s’agir soit d’un objet [CRect,](../../atl-mfc-shared/reference/crect-class.md) soit d’une structure [RECT.](/windows/win32/api/windef/ns-windef-rect)

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle du lien. Ce ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle du lien.

### <a name="return-value"></a>Valeur de retour

VRAI si l’initialisation a été couronnée de succès; autrement FALSE.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des constantes de style Windows étendues.

La deuxième forme `CreateEx` de la méthode est dépréciée. Utilisez le premier formulaire qui spécifie le paramètre *lpszLinkMarkup.*

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>CLinkCtrl::GetIdealHeight

Récupère la hauteur idéale du contrôle du lien.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Valeur de retour

La hauteur idéale du contrôle, en pixels.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight), tel que décrit dans le SDK Windows.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>CLinkCtrl::GetIdealSize

Calcule la hauteur préférée du texte de lien pour le contrôle de lien actuel, selon la largeur spécifiée du lien.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*cxMaxWidth*|[dans] La largeur maximale du lien, en pixels.|
|[out] \* *pSize*|Un pointeur vers une structure Windows [SIZE.](/windows/win32/api/windef/ns-windef-size) Lorsque cette méthode revient, le `SIZE` membre *cy* de la structure contient la hauteur de texte de lien idéal pour la largeur de texte de lien qui est spécifié par *cxMaxWidth*. Le membre *cx* de la structure contient la largeur de texte de lien qui est réellement nécessaire.|

### <a name="return-value"></a>Valeur de retour

La hauteur préférée du texte de lien, en pixels. La valeur de rendement est la même que `SIZE` la valeur du membre *cy* de la structure.

### <a name="remarks"></a>Notes

Pour un exemple `GetIdealSize` de la méthode, voir l’exemple dans [CLinkCtrl::Créer](#create).

Cette méthode envoie le [message LM_GETIDEALSIZE,](/windows/win32/Controls/lm-getidealsize) qui est décrit dans le SDK Windows.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>CLinkCtrl::GetItem

Récupère les états et les attributs d’un élément de contrôle de lien.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Un pointeur vers une structure [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) pour recevoir des informations sur l’élément.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem), tel que décrit dans le SDK Windows.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>CLinkCtrl::GetItemID

Récupère l’ID d’un élément de contrôle de lien.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Paramètres

*Ilink*<br/>
L’index d’un élément de contrôle de lien.

*strID*<br/>
Un objet [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’ID de l’élément spécifié.

*szID szID*<br/>
Une chaîne non terminée contenant l’ID de l’élément spécifié.

*cchID (en)*<br/>
La taille dans les caractères du tampon *szID.*

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

> [!NOTE]
> Cette fonction renvoie également FALSE si le tampon de *szID ou strID* est plus petit que MAX_LINKID_TEXT.

### <a name="remarks"></a>Notes

Récupère l’ID d’un élément de contrôle de lien spécifique. Pour plus d’informations, voir le message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) dans le SDK Windows.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>CLinkCtrl::GetItemState

Récupère l’état de l’élément de contrôle du lien.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Paramètres

*Ilink*<br/>
L’index d’un élément de contrôle de lien.

*pnState (En)*<br/>
La valeur de l’élément d’état spécifié.

*stateMask*<br/>
Combinaison de drapeaux décrivant l’élément d’état à obtenir. Pour une liste de valeurs, `state` voir la description du membre dans la structure [LITEM.](/windows/win32/api/commctrl/ns-commctrl-litem) Les articles admissibles sont identiques à ceux autorisés . `state`

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Récupère la valeur de l’élément d’état spécifié d’un élément de contrôle de lien spécifique. Pour plus d’informations, voir le message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) dans le SDK Windows.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>CLinkCtrl::GetItemUrl

Récupère l’URL représentée par l’élément de contrôle du lien.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Paramètres

*Ilink*<br/>
L’index d’un élément de contrôle de lien.

*strUrl*<br/>
Un objet [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’URL représentée par l’élément spécifié

*szUrl*<br/>
Une chaîne non terminée contenant l’URL représentée par l’élément spécifié

*cchUrl*<br/>
La taille dans les caractères du tampon *szURL.*

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

> [!NOTE]
> Cette fonction renvoie également FALSE si le tampon de *szUrl ou strUrl* est plus petit que MAX_LINKID_TEXT.

### <a name="remarks"></a>Notes

Récupère l’URL représentée par l’élément de contrôle de lien spécifié. Pour plus d’informations, voir le message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) dans le SDK Windows.

## <a name="clinkctrlhittest"></a><a name="hittest"></a>CLinkCtrl::HitTest

Détermine si l’utilisateur a cliqué sur le lien spécifié.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Paramètres

*phti phti*<br/>
Pointeur `LHITTESTINFO` vers une structure contenant des informations sur le lien que l’utilisateur a cliqué.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [LM_HITTEST](/windows/win32/Controls/lm-hittest), tel que décrit dans le SDK Windows.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>CLinkCtrl::SetItem

Définit les états et les attributs d’un élément de contrôle de lien.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Un pointeur vers une structure [LITEM](/windows/win32/api/commctrl/ns-commctrl-litem) contenant les informations à définir.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Cette fonction de membre implémente le comportement du message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem), tel que décrit dans le SDK Windows.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>CLinkCtrl::SetItemID

Récupère l’ID d’un élément de contrôle de lien.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Paramètres

*Ilink*<br/>
L’index d’un élément de contrôle de lien.

*szID szID*<br/>
Une chaîne non terminée contenant l’ID de l’élément spécifié.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Définit l’ID d’un élément de contrôle de lien spécifique. Pour plus d’informations, consultez le message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) dans le SDK Windows.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>CLinkCtrl::SetItemState

Récupère l’état de l’élément de contrôle du lien.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Paramètres

*Ilink*<br/>
L’index d’un élément de contrôle de lien.

*pnState (En)*<br/>
La valeur de l’élément d’état spécifié en cours d’ensemble.

*stateMask*<br/>
Combinaison de drapeaux décrivant l’élément d’état en cours d’ensemble. Pour une liste de valeurs, `state` voir la description du membre dans la structure [LITEM.](/windows/win32/api/commctrl/ns-commctrl-litem) Les articles admissibles sont identiques à ceux autorisés . `state`

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Définit la valeur de l’élément d’état spécifié d’un élément de contrôle de lien spécifique. Pour plus d’informations, consultez le message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) dans le SDK Windows.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>CLinkCtrl::SetItemUrl

Définit l’URL représentée par l’élément de contrôle du lien.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*Ilink*<br/>
L’index d’un élément de contrôle de lien.

*szUrl*<br/>
Une chaîne non terminée contenant l’URL représentée par l’élément spécifié

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Définit l’URL représentée par l’élément de contrôle de lien spécifié. Pour plus d’informations, consultez le message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
