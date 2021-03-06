---
description: 'En savoir plus sur : classe CMFCRibbonLinkCtrl'
title: CMFCRibbonLinkCtrl, classe
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
ms.openlocfilehash: 19b10643fa1af25dae4a5dc888f61d1c9ecaaee7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321784"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl, classe

Implémente un lien hypertexte qui est positionné sur un ruban. Le lien hypertexte ouvre une page web lorsque vous cliquez dessus.
Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

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
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Substitue [CMFCRibbonButton :: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Retourne la valeur du lien hypertexte.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Substitue [CMFCRibbonButton :: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Substitue [CMFCRibbonButton :: GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Substitue `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Substitue [CMFCRibbonButton :: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Substitue [CMFCRibbonBaseElement :: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Substitue `CMFCRibbonButton::OnMouseMove`.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Ouvre la page web spécifiée dans le lien hypertexte.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Définit la valeur du lien hypertexte.|

## <a name="remarks"></a>Notes

Après avoir créé un lien hypertexte, ajoutez-le à un panneau en appelant [CMFCRibbonPanel :: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxRibbonLinkCtrl. h

## <a name="cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a> CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Construit et initialise un objet [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) .

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans Spécifie l’ID de commande de la commande qui s’exécute lorsque l’utilisateur clique sur le contrôle de lien.

*lpszText*<br/>
dans Spécifie l’étiquette à afficher sur le contrôle de lien.

*lpszLink*<br/>
dans Spécifie le lien hypertexte associé au contrôle de lien.

### <a name="example"></a>Exemple

L’exemple suivant montre comment utiliser le constructeur de la `CMFCRibbonLinkCtrl` classe. Cet extrait de code fait partie de l' [exemple de gadgets de ruban](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

## <a name="cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a> CMFCRibbonLinkCtrl :: CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

dans *src*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a> CMFCRibbonLinkCtrl :: GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a> CMFCRibbonLinkCtrl::GetLink

Retourne la valeur du lien hypertexte.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Valeur renvoyée

Valeur actuelle du lien hypertexte.

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a> CMFCRibbonLinkCtrl :: GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a> CMFCRibbonLinkCtrl :: GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a> CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Paramètres

dans *&#42;* de capture de données modifiées<br/>
dans *CRect*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a> CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a> CMFCRibbonLinkCtrl :: OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a> CMFCRibbonLinkCtrl :: OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Paramètres

dans *point*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a> CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Notes

## <a name="cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a> CMFCRibbonLinkCtrl::OpenLink

Ouvre la page web spécifiée dans le lien hypertexte.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la page Web associée a été ouverte avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Ouvre une page Web à l’aide du lien hypertexte associé à l' `CMFCRibbonLinkCtrl` objet.

## <a name="cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a> CMFCRibbonLinkCtrl::SetLink

Définit la valeur du lien hypertexte.

```cpp
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Paramètres

*lpszLink*<br/>
dans Spécifie le texte du lien hypertexte.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)
