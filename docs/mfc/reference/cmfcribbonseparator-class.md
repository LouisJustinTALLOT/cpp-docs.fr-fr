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
ms.openlocfilehash: de2c6c45e4a91aa4efa0ebacba4019be74e03c72
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560866"
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
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Ajoute un séparateur à la liste **commandes** de la boîte de dialogue **personnaliser** . (Substitue [CMFCRibbonBaseElement :: AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|
|`CMFCRibbonSeparator::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|`CMFCRibbonSeparator::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|

### <a name="protected-methods"></a>Méthodes protégées

|||
|-|-|
|Nom|Description|
|[CMFCRibbonSeparator :: CopyFrom](#copyfrom)|Méthode de copie qui définit les variables de membre d’un séparateur à partir d’un autre objet.|
|[CMFCRibbonSeparator :: GetRegularSize](#getregularsize)|Retourne la taille d’un séparateur.|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Indique s’il s’agit d’un séparateur.|
|[CMFCRibbonSeparator :: IsTabStop](#istabstop)|Indique s’il s’agit d’un taquet de tabulation.|
|[CMFCRibbonSeparator :: OnDraw](#ondraw)|Appelée par le système pour dessiner le séparateur sur le ruban ou la barre d’outils accès rapide.|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Appelée par le système pour dessiner le séparateur dans la liste **commandes** .|

## <a name="remarks"></a>Notes

Un séparateur de ruban est une ligne verticale ou horizontale qui sépare logiquement les éléments du ruban. Un séparateur peut être dessiné sur le contrôle du ruban, dans le menu principal de l’application, dans la barre d’État du ruban et dans la barre d’outils accès rapide.

Pour utiliser un séparateur dans votre application, construisez le nouvel objet et ajoutez-le au menu principal de l’application, comme illustré ici :

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```

Appelez [CMFCRibbonPanel :: AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) pour ajouter des séparateurs aux panneaux du ruban. Les séparateurs sont alloués et ajoutés en interne par la `AddSeparator` méthode.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxbaseribbonelement.h

## <a name="cmfcribbonseparatoraddtolistbox"></a><a name="addtolistbox"></a> CMFCRibbonSeparator::AddToListBox

Ajoute un séparateur à la liste **commandes** de la boîte de dialogue **personnaliser** .

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>Paramètres

*pWndListBox*<br/>
dans Pointeur vers la liste de **commandes** dans laquelle le séparateur est ajouté.

*bDeep*<br/>
dans Pas.

### <a name="return-value"></a>Valeur de retour

Index de base zéro de la chaîne dans la zone de liste spécifiée par *pWndListBox*.

## <a name="cmfcribbonseparatorcmfcribbonseparator"></a><a name="cmfcribbonseparator"></a> CMFCRibbonSeparator::CMFCRibbonSeparator

Construit un objet `CMFCRibbonSeparator`.

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>Paramètres

*bIsHoriz*<br/>
dans Si la valeur est TRUE, le séparateur est horizontal ; Si la valeur est FALSe, le séparateur est vertical.

### <a name="remarks"></a>Notes

Les séparateurs horizontaux sont utilisés dans les menus de l’application. Les séparateurs verticaux sont utilisés dans les barres d’outils.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire un objet de la `CMFCRibbonSeparator` classe.

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

## <a name="cmfcribbonseparatorcopyfrom"></a><a name="copyfrom"></a> CMFCRibbonSeparator :: CopyFrom

Méthode de copie qui définit les variables de membre d’un séparateur à partir d’un autre objet.

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Paramètres

*Sources*<br/>
dans Élément de ruban source à partir duquel effectuer la copie.

## <a name="cmfcribbonseparatorgetregularsize"></a><a name="getregularsize"></a> CMFCRibbonSeparator :: GetRegularSize

Retourne la taille d’un séparateur.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contenu d’appareil.

### <a name="return-value"></a>Valeur de retour

Taille du séparateur sur le contexte de périphérique donné.

## <a name="cmfcribbonseparatorisseparator"></a><a name="isseparator"></a> CMFCRibbonSeparator::IsSeparator

Indique s’il s’agit d’un séparateur.

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours TRUE pour cette classe.

## <a name="cmfcribbonseparatoristabstop"></a><a name="istabstop"></a> CMFCRibbonSeparator :: IsTabStop

Indique s’il s’agit d’un taquet de tabulation.

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>Valeur de retour

Toujours FALSe pour cette classe.

### <a name="remarks"></a>Notes

Un séparateur de ruban n’est pas un taquet de tabulation.

## <a name="cmfcribbonseparatorondraw"></a><a name="ondraw"></a> CMFCRibbonSeparator :: OnDraw

Appelée par le système pour dessiner le séparateur sur le ruban ou la barre d’outils accès rapide.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique (Device Context).

## <a name="cmfcribbonseparatorondrawonlist"></a><a name="ondrawonlist"></a> CMFCRibbonSeparator::OnDrawOnList

Appelée par le système pour dessiner le séparateur dans la liste **commandes** .

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

*Maîtres*\
dans Pointeur vers un contexte de périphérique (Device Context).

*strText*\
dans Texte affiché dans la liste.

*nTextOffset*\
dans Espacement entre le texte et le côté gauche du rectangle englobant.

*rectangulaire*\
dans Spécifie le rectangle englobant.

*bIsSelected*\
dans Pas.

*bHighlighted*\
dans Pas.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
