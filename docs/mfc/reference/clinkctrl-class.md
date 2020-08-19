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
ms.openlocfilehash: 80548015ff9f24127280ee94421c8fbda7a647ea
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561412"
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
|[CLinkCtrl :: CLinkCtrl](#clinkctrl)|Construit un objet `CLinkCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CLinkCtrl :: Create](#create)|Crée un contrôle de lien et l’attache à un `CLinkCtrl` objet.|
|[CLinkCtrl :: CreateEx](#createex)|Crée un contrôle de lien avec des styles étendus et l’attache à un `CLinkCtrl` objet.|
|[CLinkCtrl :: GetIdealHeight](#getidealheight)|Récupère la hauteur idéale du contrôle de lien.|
|[CLinkCtrl :: GetIdealSize](#getidealsize)|Calcule la hauteur par défaut du texte de lien pour le contrôle de lien actif, en fonction de la largeur spécifiée du lien.|
|[CLinkCtrl :: GetItem](#getitem)|Récupère les États et les attributs d’un élément de contrôle de lien.|
|[CLinkCtrl :: GetItemID](#getitemid)|Récupère l’ID d’un élément de contrôle de lien.|
|[CLinkCtrl :: GetItemState](#getitemstate)|Récupère l’état de l’élément de contrôle de lien.|
|[CLinkCtrl :: GetItemUrl](#getitemurl)|Récupère l’URL représentée par l’élément de contrôle de lien.|
|[CLinkCtrl :: HitTest](#hittest)|Détermine si l’utilisateur a cliqué sur le lien spécifié.|
|[CLinkCtrl :: SetItem](#setitem)|Définit les États et les attributs d’un élément de contrôle de lien.|
|[CLinkCtrl :: SetItemID](#setitemid)|Définit l’ID d’un élément de contrôle de lien.|
|[CLinkCtrl :: SetItemState](#setitemstate)|Définit l’état de l’élément de contrôle de lien.|
|[CLinkCtrl :: SetItemUrl](#setitemurl)|Définit l’URL représentée par l’élément de contrôle de lien.|

## <a name="remarks"></a>Notes

Un « contrôle de lien » offre un moyen pratique d’incorporer des liens hypertexte dans une fenêtre. Le contrôle réel est une fenêtre qui affiche le texte marqué et lance les applications appropriées lorsque l’utilisateur clique sur un lien incorporé. Plusieurs liens sont pris en charge dans un contrôle et sont accessibles par un index de base zéro.

Ce contrôle (et par conséquent la `CLinkCtrl` classe) est uniquement disponible pour les programmes qui s’exécutent sous Windows XP et versions ultérieures.

Pour plus d’informations, consultez [Syslink Control](/windows/win32/Controls/syslink-overview) dans le SDK Windows.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Spécifications

**En-tête :** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a> CLinkCtrl :: CLinkCtrl

Construit un objet `CLinkCtrl`.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a> CLinkCtrl :: Create

Crée un contrôle de lien et l’attache à un `CLinkCtrl` objet.

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

*lpszLinkMarkup*<br/>
Pointeur vers une chaîne se terminant par zéro qui contient le texte marqué à afficher. Pour plus d’informations, consultez la section « balisage et accès aux liens » dans la rubrique [vue d’ensemble des contrôles Syslink](/windows/win32/Controls/syslink-overview).

*dwStyle*<br/>
Spécifie le style du contrôle de lien. Appliquez une combinaison de styles de contrôle. Pour plus d’informations, consultez [styles de contrôles communs](/windows/win32/Controls/common-control-styles) dans le `Windows SDK` .

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle de lien. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle de lien. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de lien.

### <a name="return-value"></a>Valeur de retour

TRUE si l’initialisation a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Vous construisez un `CLinkCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, puis appelez `Create` , qui crée le contrôle de lien et l’attache à l' `CLinkCtrl` objet. Si vous souhaitez utiliser des styles Windows étendus avec votre contrôle, appelez [CLinkCtrl :: CreateEx](#createex) à la place de `Create` .

La deuxième forme de la `Create` méthode est déconseillée. Utilisez le premier formulaire qui spécifie le paramètre *lpszLinkMarkup* .

### <a name="example"></a>Exemple

L’exemple de code suivant définit deux variables, nommées `m_Link1` et `m_Link2` , qui sont utilisées pour accéder à deux contrôles de lien.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Exemple

L’exemple de code suivant crée un contrôle de lien en fonction de l’emplacement d’un autre contrôle de lien. Le chargeur de ressources crée le premier contrôle de lien au démarrage de votre application. Lorsque votre application entre dans la méthode OnInitDialog, vous créez le deuxième contrôle de lien par rapport à la position du premier contrôle de lien. Ensuite, vous redimensionnez le deuxième contrôle de lien pour qu’il corresponde au texte qu’il affiche.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a> CLinkCtrl :: CreateEx

Crée un contrôle de lien avec des styles étendus et l’attache à un `CLinkCtrl` objet.

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

*lpszLinkMarkup*<br/>
Pointeur vers une chaîne se terminant par zéro qui contient le texte marqué à afficher. Pour plus d’informations, consultez la section « balisage et accès aux liens » dans la rubrique [vue d’ensemble des contrôles Syslink](/windows/win32/Controls/syslink-overview).

*dwExStyle*<br/>
Spécifie le style étendu du contrôle de lien. Pour obtenir la liste des styles Windows étendus, consultez le paramètre *dwExStyle* pour [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) dans le SDK Windows.

*dwStyle*<br/>
Spécifie le style du contrôle de lien. Appliquez une combinaison de styles de contrôle. Pour plus d’informations, consultez [styles de contrôle communs](/windows/win32/Controls/common-control-styles) dans le SDK Windows.

*rectangulaire*<br/>
Spécifie la taille et la position du contrôle de lien. Il peut s’agir d’un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) ou d’une structure [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Spécifie la fenêtre parente du contrôle de lien. Il ne doit pas être NULL.

*nID*<br/>
Spécifie l’ID du contrôle de lien.

### <a name="return-value"></a>Valeur de retour

TRUE si l’initialisation a réussi ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Utilisez `CreateEx` au lieu de [Create](#create) pour appliquer des constantes de style Windows étendues.

La deuxième forme de la `CreateEx` méthode est déconseillée. Utilisez le premier formulaire qui spécifie le paramètre *lpszLinkMarkup* .

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a> CLinkCtrl :: GetIdealHeight

Récupère la hauteur idéale du contrôle de lien.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Valeur de retour

Hauteur idéale du contrôle, en pixels.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)de message Win32, comme décrit dans le SDK Windows.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a> CLinkCtrl :: GetIdealSize

Calcule la hauteur par défaut du texte de lien pour le contrôle de lien actif, en fonction de la largeur spécifiée du lien.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Paramètres

*cxMaxWidth*\
dans Largeur maximale, en pixels, du lien.

*pSize*\
à Pointeur vers une structure de [taille](/windows/win32/api/windef/ns-windef-size) Windows. Lorsque cette méthode est retournée, le membre *CY* de la `SIZE` structure contient la hauteur de texte de lien idéale pour la largeur du texte de lien spécifiée par *cxMaxWidth*. Le membre *CX* de la structure contient la largeur du texte du lien qui est réellement nécessaire.

### <a name="return-value"></a>Valeur de retour

Hauteur préférée du texte du lien, en pixels. La valeur de retour est la même que la valeur du membre *CY* de la `SIZE` structure.

### <a name="remarks"></a>Notes

Pour obtenir un exemple de la `GetIdealSize` méthode, consultez l’exemple dans [CLinkCtrl :: Create](#create).

Cette méthode envoie le message [LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize) , qui est décrit dans le SDK Windows.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a> CLinkCtrl :: GetItem

Récupère les États et les attributs d’un élément de contrôle de lien.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers une structure [litem](/windows/win32/api/commctrl/ns-commctrl-litem) pour recevoir des informations sur l’élément.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [LM_GETITEM](/windows/win32/Controls/lm-getitem)de message Win32, comme décrit dans le SDK Windows.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a> CLinkCtrl :: GetItemID

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

*iLink*<br/>
Index d’un élément de contrôle de lien.

*strID*<br/>
Objet [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’ID de l’élément spécifié.

*szID*<br/>
Chaîne terminée par le caractère null qui contient l’ID de l’élément spécifié.

*cchID*<br/>
Taille en caractères de la mémoire tampon *szID* .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

> [!NOTE]
> Cette fonction retourne également FALSe si la mémoire tampon de *szID ou strID* est inférieure à MAX_LINKID_TEXT.

### <a name="remarks"></a>Notes

Récupère l’ID d’un élément de contrôle de lien spécifique. Pour plus d’informations, consultez le message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) dans le SDK Windows.

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a> CLinkCtrl :: GetItemState

Récupère l’état de l’élément de contrôle de lien.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Paramètres

*iLink*<br/>
Index d’un élément de contrôle de lien.

*pnState*<br/>
Valeur de l’élément d’état spécifié.

*stateMask*<br/>
Combinaison d’indicateurs décrivant l’élément d’État à atteindre. Pour obtenir la liste des valeurs, consultez la description du `state` membre dans la structure [litem](/windows/win32/api/commctrl/ns-commctrl-litem) . Les éléments autorisés sont identiques à ceux autorisés dans `state` .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Récupère la valeur de l’élément d’état spécifié d’un élément de contrôle de lien spécifique. Pour plus d’informations, consultez le message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) dans le SDK Windows.

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a> CLinkCtrl :: GetItemUrl

Récupère l’URL représentée par l’élément de contrôle de lien.

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

*iLink*<br/>
Index d’un élément de contrôle de lien.

*strUrl*<br/>
Objet [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) contenant l’URL représentée par l’élément spécifié.

*szUrl*<br/>
Chaîne terminée par le caractère null, contenant l’URL représentée par l’élément spécifié.

*cchUrl*<br/>
Taille en caractères de la mémoire tampon *szURL* .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

> [!NOTE]
> Cette fonction retourne également FALSe si la mémoire tampon de *szUrl ou de strURL* est inférieure à MAX_LINKID_TEXT.

### <a name="remarks"></a>Notes

Récupère l’URL représentée par l’élément de contrôle de lien spécifié. Pour plus d’informations, consultez le message Win32 [LM_GETITEM](/windows/win32/Controls/lm-getitem) dans le SDK Windows.

## <a name="clinkctrlhittest"></a><a name="hittest"></a> CLinkCtrl :: HitTest

Détermine si l’utilisateur a cliqué sur le lien spécifié.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Paramètres

*phti*<br/>
Pointeur vers une `LHITTESTINFO` structure contenant toutes les informations relatives au lien sur lequel l’utilisateur a cliqué.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [LM_HITTEST](/windows/win32/Controls/lm-hittest)de message Win32, comme décrit dans le SDK Windows.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a> CLinkCtrl :: SetItem

Définit les États et les attributs d’un élément de contrôle de lien.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers une structure [litem](/windows/win32/api/commctrl/ns-commctrl-litem) contenant les informations à définir.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Cette fonction membre implémente le comportement de la [LM_SETITEM](/windows/win32/Controls/lm-setitem)de message Win32, comme décrit dans le SDK Windows.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a> CLinkCtrl :: SetItemID

Récupère l’ID d’un élément de contrôle de lien.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Paramètres

*iLink*<br/>
Index d’un élément de contrôle de lien.

*szID*<br/>
Chaîne terminée par le caractère null qui contient l’ID de l’élément spécifié.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Définit l’ID d’un élément de contrôle de lien spécifique. Pour plus d’informations, consultez le message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) dans le SDK Windows.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a> CLinkCtrl :: SetItemState

Récupère l’état de l’élément de contrôle de lien.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Paramètres

*iLink*<br/>
Index d’un élément de contrôle de lien.

*pnState*<br/>
Valeur de l’élément d’état spécifié qui est défini.

*stateMask*<br/>
Combinaison d’indicateurs décrivant l’élément d’État en cours de définition. Pour obtenir la liste des valeurs, consultez la description du `state` membre dans la structure [litem](/windows/win32/api/commctrl/ns-commctrl-litem) . Les éléments autorisés sont identiques à ceux autorisés dans `state` .

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Définit la valeur de l’élément d’état spécifié d’un élément de contrôle de lien spécifique. Pour plus d’informations, consultez le message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) dans le SDK Windows.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a> CLinkCtrl :: SetItemUrl

Définit l’URL représentée par l’élément de contrôle de lien.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Paramètres

*iLink*<br/>
Index d’un élément de contrôle de lien.

*szUrl*<br/>
Chaîne terminée par le caractère null, contenant l’URL représentée par l’élément spécifié.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Définit l’URL représentée par l’élément de contrôle de lien spécifié. Pour plus d’informations, consultez le message Win32 [LM_SETITEM](/windows/win32/Controls/lm-setitem) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
