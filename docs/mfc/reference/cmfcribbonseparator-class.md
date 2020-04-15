---
title: CMFCRibbonSeparator, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 41a958c78719f6aedf1cc02f8e3ff5a2dbbf0e1b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368853"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator, classe

Implémente le séparateur de ruban.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|||
|-|-|
|Nom|Description|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Construit un objet `CMFCRibbonSeparator`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|Nom|Description|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Ajoute un séparateur à la liste **des commandes** dans la boîte de dialogue **Customize.** (Overrides [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonSeparator::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|

### <a name="protected-methods"></a>Méthodes protégées

|||
|-|-|
|Nom|Description|
|[CMFCRibbonSeparator::CopyDe](#copyfrom)|Méthode de copie qui définit les variables des membres d’un séparateur d’un autre objet.|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Retourne la taille d’un séparateur.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indique s’il s’agit d’un séparateur.|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Indique s’il s’agit d’un arrêt d’onglet.|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Appelé par le système pour dessiner le séparateur sur le ruban ou la barre d’outils d’accès rapide.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Appelé par le système pour dessiner le séparateur sur la liste **des commandes.**|

## <a name="remarks"></a>Notes

Un séparateur de ruban est une ligne verticale ou horizontale qui sépare logiquement les éléments de ruban. Un séparateur peut être dessiné sur le contrôle du ruban, le menu d’application principal, la barre d’état du ruban et la barre d’outils d’accès rapide.

Pour utiliser un séparateur dans votre application, construisez le nouvel objet et ajoutez-le au menu d’application principal tel qu’indiqué ici :

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Appelez [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) pour ajouter des séparateurs aux panneaux ruban. Les séparateurs sont attribués `AddSeparator` et ajoutés en interne par la méthode.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a>CMFCRibbonSeparator::AddToListBox

Ajoute un séparateur à la liste **des commandes** dans la boîte de dialogue **Customize.**

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Paramètres

*pWndListBox (en)*<br/>
[dans] Un pointeur à la liste **des commandes** où le séparateur est ajouté.

*bDeep (en)*<br/>
[dans] Ignoré.

### <a name="return-value"></a>Valeur de retour

Index basé à zéro à la chaîne dans la boîte de liste spécifiée par *pWndListBox*.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a>CMFCRibbonSeparator::CMFCRibbonSeparator

Construit un objet `CMFCRibbonSeparator`.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Paramètres

*bIsHoriz (en)*<br/>
[dans] Si VRAI, le séparateur est horizontal; si FALSE, le séparateur est vertical.

### <a name="remarks"></a>Notes

Les séparateurs horizontaux sont utilisés dans les menus d’application. Les séparateurs verticaux sont utilisés dans les barres d’outils.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCRibbonSeparator` un objet de la classe.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonSeparator::CopyDe

Méthode de copie qui définit les variables des membres d’un séparateur d’un autre objet.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

*Src (Src)*<br/>
[dans] L’élément ruban source à copier.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonSeparator::GetRegularSize

Retourne la taille d’un séparateur.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur sur le contenu d’un appareil.

### <a name="return-value"></a>Valeur de retour

La taille du séparateur sur le contexte de l’appareil donné.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a>CMFCRibbonSeparator::IsSeparator

Indique s’il s’agit d’un séparateur.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours VRAI pour cette classe.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a>CMFCRibbonSeparator::IsTabStop

Indique s’il s’agit d’un arrêt d’onglet.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours FALSE pour cette classe.

### <a name="remarks"></a>Notes

Un séparateur de ruban n’est pas un arrêt d’onglet.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a>CMFCRibbonSeparator::OnDraw

Appelé par le système pour dessiner le séparateur sur le ruban ou la barre d’outils d’accès rapide.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil.

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a>CMFCRibbonSeparator::OnDrawOnList

Appelé par le système pour dessiner le séparateur sur la liste **des commandes.**

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

|||
|-|-|
|Paramètre|Description|
|*pDC*|[dans] Un pointeur vers un contexte d’appareil.|
|*strText (en)*|[dans] Texte affiché sur la liste.|
|*nTextOffset (en anglais)*|[dans] Espacement entre le texte et le côté gauche du rectangle de délimitation.|
|*Rect*|[dans] Spécifie le rectangle de délimitation.|
|*bIsSelected*|[dans] Ignoré.|
|*bHighlighted*|[dans] Ignoré.|

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
