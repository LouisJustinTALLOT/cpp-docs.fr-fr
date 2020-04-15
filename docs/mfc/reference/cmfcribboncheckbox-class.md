---
title: CMFCRibbonCheckBox, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 089c8056afebef31ff98a435bf145566ae64fe1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375253"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox, classe

La classe `CMFCRibbonCheckBox` implémente une case à cocher que vous pouvez ajouter à un volet du ruban, une barre d'outils Accès rapide ou un menu contextuel.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(Overrides [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(Overrides [CMFCRibbonButton::GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(Overrides [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Substitue `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(Overrides [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Overrides [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Substitue `CMFCRibbonButton::OnDrawOnList`.)|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(Overrides [CMFCRibbonButton::SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Notes

Pour utiliser un `CMFCRibbonCheckBox` dans votre application, ajoutez le constructeur suivant à votre code :

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

où *nID* est l’ID de commande de la case à cocher et *lpszText* est l’étiquette de texte de la case à cocher.

Vous pouvez ajouter une case à cocher à un panneau ruban en utilisant [CMFCRibbonPanel::Ajouter](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribboncheckbox.h

## <a name="cmfcribboncheckboxcmfcribboncheckbox"></a><a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Constructeur d’un objet de la case à cocher de ruban

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
[dans] Spécifie l’id de commande.

*lpszText*<br/>
[dans] Spécifie l’étiquette de texte.

### <a name="return-value"></a>Valeur de retour

Construit un objet de la case à cocher.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCRibbonCheckBox` un objet de la classe.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

## <a name="cmfcribboncheckboxgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonCheckBox::GetCompactSize

Lorsqu’il est remplacé, obtient la taille compacte de la case à cocher.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers le CDC associé à la case à cocher.

### <a name="return-value"></a>Valeur de retour

Retourne `CSize` un objet qui contient la taille compacte de la case à cocher.

### <a name="remarks"></a>Notes

S’il n’est pas remplacé, retourne la taille intermédiaire de la case à cocher.

## <a name="cmfcribboncheckboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonCheckBox::GetIntermediateSize

Obtient la taille intermédiaire de la case à cocher.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers le CDC associé à cette case à cocher.

### <a name="return-value"></a>Valeur de retour

Un `CSize` objet contenant la taille intermédiaire de la case à cocher.

### <a name="remarks"></a>Notes

S’il n’est pas remplacé, calcule la `AFX_CHECK_BOX_DEFAULT_SIZE`taille intermédiaire comme la taille de la case à cocher par défaut ( ) plus la taille du texte, plus les marges.

## <a name="cmfcribboncheckboxgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonCheckBox::GetRegularSize

Obtient la taille régulière de la case à cocher.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers l’objet CDC associé à cette case à cocher.

### <a name="return-value"></a>Valeur de retour

Retourne `CSize` un objet qui contient la taille régulière de la case à cocher.

### <a name="remarks"></a>Notes

S’il n’est pas remplacé, retourne la taille intermédiaire de la case à cocher.

## <a name="cmfcribboncheckboxisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Indique s’il existe une image de pointe associée à la case à cocher.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI s’il y a une image de bout d’outil associée à la case à cocher, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncheckboxondraw"></a><a name="ondraw"></a>CMFCRibbonCheckBox::OnDraw

Appelé par le cadre pour dessiner la case à cocher à l’aide d’un contexte d’appareil spécifié.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur vers le CDC dans lequel tirer la case à cocher.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncheckboxondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Appelé par le cadre pour dessiner une image de menu pour la case à cocher.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Paramètres

[dans] *&#42;des CDC*<br/>
Pointeur vers le CDC associé à la case à cocher.

*CRect*<br/>
[dans] Un `CRect` objet spécifiant le rectangle dans lequel dessiner l’image du menu.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si l’image a été dessinée, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

S’il n’est pas remplacé, retourne FALSE.

## <a name="cmfcribboncheckboxondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Appelé par le cadre pour dessiner la case à cocher dans une boîte de liste de commandes.

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Pointeur sur le contexte de l’appareil dans lequel dessiner la case à cocher.

*strText (en)*<br/>
[in] Texte d'affichage.

*nTextOffset (en anglais)*<br/>
[dans] La distance, en pixels, du côté gauche de la boîte de liste au texte d’affichage.

*Rect*<br/>
[dans] Le rectangle d’affichage pour la case à cocher.

*bIsSelected*<br/>
[dans] VRAI si la case à cocher est sélectionnée, ou FALSE si ce n’est pas le cas.

*bHighlighted*<br/>
[dans] VRAI si la case à cocher est mise en surbrillance, ou FALSE si ce n’est pas le cas.

### <a name="remarks"></a>Notes

## <a name="cmfcribboncheckboxsetaccdata"></a><a name="setaccdata"></a>CMFCRibbonCheckBox::SetACCData

Définit les données d’accessibilité pour la case à cocher.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
La fenêtre parente de la case à cocher.

*data*<br/>
Les données d’accessibilité pour la case à cocher.

### <a name="return-value"></a>Valeur de retour

Retourne toujours VRAI.

### <a name="remarks"></a>Notes

Par défaut, cette méthode définit les données d’accessibilité pour la case à cocher et renvoie toujours VRAI. Remplacez cette méthode pour définir l’accessibilité des données et retourner une valeur qui indique la réussite ou l’échec.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)
