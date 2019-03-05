---
title: Cmfcribbonlinkctrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
ms.openlocfilehash: 9f47e5a3a25120370bd618ac3a89de76761fa61a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287789"
---
# <a name="cmfcribbonlinkctrl-class"></a>Cmfcribbonlinkctrl, classe

Implémente un lien hypertexte qui est positionné sur un ruban. Le lien hypertexte ouvre une page web lorsque vous cliquez dessus.
Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Construit et initialise un objet `CMFCRibbonLinkCtrl`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Substitue `CMFCRibbonButton::CopyFrom`.)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Substitue [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Retourne la valeur du lien hypertexte.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Substitue [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Substitue [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Substitue `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Substitue [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Substitue [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Substitue `CMFCRibbonButton::OnMouseMove`.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Ouvre la page web spécifiée dans le lien hypertexte.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Définit la valeur du lien hypertexte.|

## <a name="remarks"></a>Notes

Une fois que vous créez un lien hypertexte, ajoutez-le à un panneau en appelant [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxRibbonLinkCtrl.h

##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Crée et initialise un [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) objet.

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[in] Spécifie l’ID de commande de la commande qui s’exécute lorsque l’utilisateur clique sur le contrôle de lien.

*lpszText*<br/>
[in] Spécifie l’étiquette à afficher sur le contrôle de lien.

*lpszLink*<br/>
[in] Spécifie le lien hypertexte associé au contrôle de lien.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le constructeur de la `CMFCRibbonLinkCtrl` classe. Cet extrait de code fait partie de la [exemples de Gadgets de ruban](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonLinkCtrl::CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

[in] *src*<br/>

### <a name="remarks"></a>Notes

##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[in] *pDC*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="getlink"></a>  CMFCRibbonLinkCtrl::GetLink

Retourne la valeur du lien hypertexte.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Valeur de retour

La valeur actuelle du lien hypertexte.

### <a name="remarks"></a>Notes

##  <a name="getregularsize"></a>  CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[in] *pDC*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="gettooltiptext"></a>  CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ondrawmenuimage"></a>  CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Paramètres

[in] *Capture de données modifiées&#42;*<br/>
[in] *CRect*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[in] *pDC*<br/>

### <a name="remarks"></a>Notes

##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Paramètres

[in] *point*<br/>

### <a name="remarks"></a>Notes

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Notes

##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink

Ouvre la page web spécifiée dans le lien hypertexte.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Valeur de retour

TRUE si la page Web associée a été ouvert avec succès ; Sinon, FALSE.

### <a name="remarks"></a>Notes

Ouvre une page Web à l’aide du lien hypertexte associé à la `CMFCRibbonLinkCtrl` objet.

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

Définit la valeur du lien hypertexte.

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Paramètres

*lpszLink*<br/>
[in] Spécifie le texte du lien hypertexte.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
