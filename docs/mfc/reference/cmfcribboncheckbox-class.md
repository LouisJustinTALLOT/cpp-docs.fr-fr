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
ms.openlocfilehash: a8048f860a2cce75c37a065cfdd2751141054f1b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446235"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox, classe

La classe `CMFCRibbonCheckBox` implémente une case à cocher que vous pouvez ajouter à un volet du ruban, une barre d'outils Accès rapide ou un menu contextuel.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CMFCRibbonCheckBox :: GetCompactSize](#getcompactsize)|(Substitue [CMFCRibbonButton :: GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonCheckBox :: GetIntermediateSize](#getintermediatesize)|(Substitue [CMFCRibbonButton :: GetIntermediateSize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize).)|
|[CMFCRibbonCheckBox :: GetRegularSize](#getregularsize)|(Substitue [CMFCRibbonButton :: GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|(Substitue `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonCheckBox :: OnDraw](#ondraw)|(Substitue [CMFCRibbonButton :: OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(Substitue [CMFCRibbonBaseElement :: OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|(Substitue `CMFCRibbonButton::OnDrawOnList`.)|
|[CMFCRibbonCheckBox :: SetACCData](#setaccdata)|(Substitue [CMFCRibbonButton :: SetACCData](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata).)|

## <a name="remarks"></a>Notes

Pour utiliser un `CMFCRibbonCheckBox` dans votre application, ajoutez le constructeur suivant à votre code :

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```

où *nid* est l’ID de commande de la case à cocher et *lpszText* est l’étiquette de texte de la case à cocher.

Vous pouvez ajouter une case à cocher à un volet du ruban à l’aide de [CMFCRibbonPanel :: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribboncheckbox. h

##  <a name="cmfcribboncheckbox"></a>CMFCRibbonCheckBox::CMFCRibbonCheckBox

Constructeur d’un objet de case à cocher de ruban

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Paramètres

*nID*<br/>
dans Spécifie l’ID de la commande.

*lpszText*<br/>
dans Spécifie l’étiquette de texte.

### <a name="return-value"></a>Valeur de retour

Construit un objet de case à cocher de ruban.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la classe `CMFCRibbonCheckBox`.

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>CMFCRibbonCheckBox :: GetCompactSize

En cas de substitution, obtient la taille compacte de la case à cocher.

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers le CDC associé à la case à cocher.

### <a name="return-value"></a>Valeur de retour

Retourne un objet `CSize` qui contient la taille compacte de la case à cocher.

### <a name="remarks"></a>Notes

S’il n’est pas substitué, retourne la taille intermédiaire de la case à cocher.

##  <a name="getintermediatesize"></a>CMFCRibbonCheckBox :: GetIntermediateSize

Obtient la taille intermédiaire de la case à cocher.

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers le CDC associé à cette case à cocher.

### <a name="return-value"></a>Valeur de retour

Objet `CSize` contenant la taille intermédiaire de la case à cocher.

### <a name="remarks"></a>Notes

S’il n’est pas substitué, calcule la taille intermédiaire comme taille de case à cocher par défaut (`AFX_CHECK_BOX_DEFAULT_SIZE`) plus la taille du texte, plus les marges.

##  <a name="getregularsize"></a>CMFCRibbonCheckBox :: GetRegularSize

Obtient la taille normale de la case à cocher.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers l’objet CDC associé à cette case à cocher.

### <a name="return-value"></a>Valeur de retour

Retourne un objet `CSize` qui contient la taille normale de la case à cocher.

### <a name="remarks"></a>Notes

S’il n’est pas substitué, retourne la taille intermédiaire de la case à cocher.

##  <a name="isdrawtooltipimage"></a>CMFCRibbonCheckBox::IsDrawTooltipImage

Indique si une image d’info-bulle est associée à la case à cocher.

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si une image d’info-bulle est associée à la case à cocher, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="ondraw"></a>CMFCRibbonCheckBox :: OnDraw

Appelé par l’infrastructure pour dessiner la case à cocher à l’aide d’un contexte de périphérique spécifié.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Pointeur vers le CDC dans lequel dessiner la case à cocher.

### <a name="remarks"></a>Notes

##  <a name="ondrawmenuimage"></a>CMFCRibbonCheckBox::OnDrawMenuImage

Appelé par l’infrastructure pour dessiner une image de menu pour la case à cocher.

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Paramètres

dans *CDC&#42;*<br/>
Pointeur vers le CDC associé à la case à cocher.

*CRect*<br/>
dans Objet `CRect` spécifiant le rectangle dans lequel dessiner l’image de menu.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si l’image a été dessinée, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

S’il n’est pas substitué, retourne FALSe.

##  <a name="ondrawonlist"></a>CMFCRibbonCheckBox::OnDrawOnList

Appelé par l’infrastructure pour dessiner la case à cocher dans une zone de liste commandes.

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
dans Pointeur vers le contexte de périphérique dans lequel la case à cocher doit être dessinée.

*strText*<br/>
[in] Texte d'affichage.

*nTextOffset*<br/>
dans Distance, en pixels, entre le côté gauche de la zone de liste et le texte affiché.

*rectangulaire*<br/>
dans Rectangle d’affichage de la case à cocher.

*bIsSelected*<br/>
dans TRUE si la case à cocher est activée, ou FALSe dans le cas contraire.

*bHighlighted*<br/>
dans TRUE si la case à cocher est mise en surbrillance, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

##  <a name="setaccdata"></a>CMFCRibbonCheckBox :: SetACCData

Définit les données d’accessibilité pour la case à cocher.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Paramètres

*pParent*<br/>
Fenêtre parente de la case à cocher.

*data*<br/>
Données d’accessibilité de la case à cocher.

### <a name="return-value"></a>Valeur de retour

Retourne toujours la valeur TRUE.

### <a name="remarks"></a>Notes

Par défaut, cette méthode définit les données d’accessibilité pour la case à cocher et retourne toujours la valeur TRUE. Remplacez cette méthode pour définir l’accessibilité des données et retourner une valeur qui indique la réussite ou l’échec.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel, classe](../../mfc/reference/cmfcribbonpanel-class.md)
