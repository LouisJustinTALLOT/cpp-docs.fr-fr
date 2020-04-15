---
title: Classe CRichEditView
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: 2d832f3cc07d39ace9e679901c5344a376cea03c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318639"
---
# <a name="cricheditview-class"></a>Classe CRichEditView

Avec [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) et [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), fournit la fonctionnalité du contrôle d’édition riche dans le cadre de l’architecture de vue de document de MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Construit un objet `CRichEditView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Déplace une boîte de dialogue de sorte qu’elle n’obscurcit pas la sélection actuelle.|
|[CRichEditView::CanPaste](#canpaste)|Indique si le Clipboard contient des données qui peuvent être collées dans la vue d’édition riche.|
|[CRichEditView::DoPaste](#dopaste)|Passe un élément OLE dans cette vue d’édition riche.|
|[CRichEditView::FindText](#findtext)|Trouve le texte spécifié, invoquant le curseur d’attente.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Trouve le texte spécifié.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Récupère les attributs de formatage de caractères pour la sélection actuelle.|
|[CRichEditView::GetDocument](#getdocument)|Récupère un pointeur à la [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)connexes .|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Récupère l’élément OLE qui est actuellement actif dans la vue d’édition riche.|
|[CRichEditView::GetMargins](#getmargins)|Récupère les marges de cette vue d’édition riche.|
|[CRichEditView::GetPageRect](#getpagerect)|Récupère le rectangle de page pour cette vue d’édition riche.|
|[CRichEditView::GetPaperSize](#getpapersize)|Récupère la taille du papier pour cette vue d’édition riche.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Récupère les attributs de formatage du paragraphe pour la sélection actuelle.|
|[CRichEditView::GetPrintRect](#getprintrect)|Récupère le rectangle d’impression pour cette vue d’édition riche.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Récupère la largeur de l’impression pour cette vue d’édition riche.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Récupère le contrôle d’édition riche.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Récupère l’élément sélectionné à partir de la vue d’édition riche.|
|[CRichEditView::GetTextLength](#gettextlength)|Récupère la longueur du texte dans la vue d’édition riche.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Récupère le nombre de caractères ou d’octets dans la vue d’édition riche. Liste élargie du drapeau pour la méthode de détermination de la longueur.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Insère un fichier sous forme d’élément OLE.|
|[CRichEditView::InsertItem](#insertitem)|Insère un nouvel élément comme élément OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Indique si le Clipboard contient des données dans un format de modification ou de texte riche.|
|[CRichEditView::SurCharEffect](#onchareffect)|Toggles le formatage de caractère pour la sélection actuelle.|
|[CRichEditView::OnParaAlign](#onparaalign)|Modifie l’alignement des paragraphes.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Mise à jour de l’interface utilisateur de commande pour les fonctions des membres du public de caractère.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Mise à jour de l’interface utilisateur de commande pour les fonctions des membres du public paragraphe.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Formate le texte spécifié dans le rectangle donné.|
|[CRichEditView::PrintPage](#printpage)|Formate le texte spécifié dans la page donnée.|
|[CRichEditView::SetCharFormat](#setcharformat)|Définit les attributs de formatage des personnages pour la sélection actuelle.|
|[CRichEditView::SetMargins](#setmargins)|Définit les marges de cette vue d’édition riche.|
|[CRichEditView::SetPaperSize](#setpapersize)|Définit la taille du papier pour cette vue d’édition riche.|
|[CRichEditView::SetParaFormat](#setparaformat)|Définit les attributs de formatage des paragraphes pour la sélection actuelle.|
|[CRichEditView::TextNotFound](#textnotfound)|Réinitialise l’état de recherche interne du contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Récupère un objet Clipboard pour une gamme dans cette vue d’édition riche.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Récupère un menu contextuelle à utiliser sur un bouton de souris droite vers le bas.|
|[CRichEditView::Isselected](#isselected)|Indique si l’élément OLE donné est sélectionné ou non.|
|[CRichEditView::OnFindNext](#onfindnext)|Trouve l’occurrence suivante d’un sous-corde.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Rafraîchit une vue lorsqu’elle est jointe pour la première fois à un document.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Récupère les données natives d’un élément OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Définit les caractéristiques d’impression de l’appareil donné.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Remplace tous les occurrences d’une chaîne donnée par une nouvelle chaîne.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Remplace la sélection actuelle.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Gère la notification de l’utilisateur que le texte demandé n’a pas été trouvé.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Questions à voir sur les `IDataObject`données sur le .|
|[CRichEditView::WrapChanged](#wrapchanged)|Ajuste le périphérique de sortie cible pour cette `m_nWordWrap`vue d’édition riche, basée sur la valeur de .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Indique la quantité d’en retrait pour les listes de balles.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Indique les contraintes de papier d’enveloppe du mot.|

## <a name="remarks"></a>Notes

Un « contrôle d’édition riche » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier le texte. Le texte peut être attribué formatage de caractère et de paragraphe, et peut inclure des objets OLE intégrés. Les contrôles d’édition riches fournissent une interface de programmation pour le formatage du texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour mettre les opérations de formatage à la disposition de l’utilisateur.

`CRichEditView`conserve le texte et la caractéristique de formatage du texte. `CRichEditDoc`maintient la liste des éléments clients OLE qui sont dans la vue. `CRichEditCntrItem`offre un accès côté conteneur à l’article client OLE.

Ce contrôle Windows Common (et donc le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes connexes) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT versions 3.51 et plus tard.

Par exemple, à l’aide d’une vue d’édition riche dans une application MFC, consultez l’application [d’échantillon WORDPAD.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>CRichEditView::AdjustDialogPosition

Appelez cette fonction pour déplacer la boîte de dialogue donnée afin qu’elle n’obscurcisse pas la sélection actuelle.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Paramètres

*pDlg (en)*<br/>
Pointeur `CDialog` vers un objet.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>CRichEditView::CanPaste

Appelez cette fonction pour déterminer si le Clipboard contient des informations qui peuvent être collées dans cette vue d’édition riche.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le Clipboard contient des données dans un format que cette vue d’édition riche peut accepter; autrement, 0.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>CRichEditView::CRichEditView

Appelez cette fonction `CRichEditView` pour créer un objet.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>CRichEditView::DoPaste

Appelez cette fonction pour coller l’élément OLE dans *dataobj* dans ce document/vue d’édition riche.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Paramètres

*dataobj (en)*<br/>
Le [COleDataObject](../../mfc/reference/coledataobject-class.md) contenant les données à coller.

*Cf*<br/>
Le format Clipboard souhaité.

*hMetaPict (en)*<br/>
Le metafile qui représente l’élément à coller.

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction dans le cadre de la mise en œuvre par défaut de [QueryAcceptData](#queryacceptdata).

Cette fonction détermine le type de pâte en fonction des résultats du gestionnaire de Pâte Spéciale. Si *cf* est 0, le nouvel article utilise la représentation iconique actuelle. Si *cf* est nonzero et *hMetaPict* n’est pas NULL, le nouvel élément utilise *hMetaPict* pour sa représentation.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>CRichEditView::FindText

Appelez cette fonction pour trouver le texte spécifié et définissez-le comme la sélection actuelle.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Contient la chaîne à rechercher.

*bCase*<br/>
Indique si la recherche est sensible aux cas.

*bWord (en)*<br/>
Indique si la recherche doit correspondre à des mots entiers seulement, pas des parties de mots.

*bNext (en)*<br/>
Indique la direction de la recherche. Si VRAI, la direction de recherche est vers la fin du tampon. Si FALSE, la direction de recherche est vers le début du tampon.

### <a name="return-value"></a>Valeur de retour

Nonzero si le texte *lpszFind* est trouvé; sinon 0.

### <a name="remarks"></a>Notes

Cette fonction affiche le curseur d’attente pendant l’opération de recherche.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>CRichEditView::FindTextSimple

Appelez cette fonction pour trouver le texte spécifié et définissez-le comme la sélection actuelle.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Contient la chaîne à rechercher.

*bCase*<br/>
Indique si la recherche est sensible aux cas.

*bWord (en)*<br/>
Indique si la recherche doit correspondre à des mots entiers seulement, pas des parties de mots.

*bNext (en)*<br/>
Indique la direction de la recherche. Si VRAI, la direction de recherche est vers la fin du tampon. Si FALSE, la direction de recherche est vers le début du tampon.

### <a name="return-value"></a>Valeur de retour

Nonzero si le texte *lpszFind* est trouvé; sinon 0.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection

Appelez cette fonction pour obtenir les attributs de formatage de caractère de la sélection actuelle.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Valeur de retour

Une structure [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) qui contient les attributs de formatage des personnages de la sélection actuelle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le message [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) et la structure [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>CRichEditView::GetClipboardData

Le cadre appelle cette fonction dans le cadre du traitement de [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Paramètres

*lpchrg lpchrg*<br/>
Pointeur vers la structure [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) spécifiant la gamme de caractères (et d’éléments OLE) à copier à l’objet de données spécifié par *lplpdataobj*.

*dwReco*<br/>
Drapeau d’opération de clipboard. Peut être l’une de ces valeurs.

- RECO_COPY Copie au Clipboard.

- RECO_CUT Couper sur le Clipboard.

- RECO_DRAG’opération Drag (drag and drop).

- RECO_DROP Drop (drag and drop).

- RECO_PASTE pâte du Clipboard.

*lpRichDataObj*<br/>
Pointeur vers un objet [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) contenant les données Clipboard du contrôle d’édition riche ( [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj lplpdataobj*<br/>
Pointeur à la variable de `IDataObject` pointeur qui reçoit l’adresse de l’objet représentant la plage spécifiée dans le paramètre *lpchrg.* La valeur de *lplpdataobj* est ignorée si une erreur est retournée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT signalant le succès de l’opération. Pour plus d’informations sur HRESULT, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

### <a name="remarks"></a>Notes

Si la valeur de `IRichEditOleCallback::GetClipboardData` rendement `IDataObject` indique le succès, retourne le accessible par *lplpdataobj*; sinon, il retourne celui accessible par *lpRichDataObj*. Remplacez cette fonction pour fournir vos propres données Clipboard. La mise en œuvre par défaut de cette fonction revient E_NOTIMPL.

C’est un avancé primordial.

Pour plus d’informations, voir [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata), et [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) dans le SDK Windows et voir [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) dans le SDK Windows.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>CRichEditView::GetContextMenu

Le cadre appelle cette fonction dans le cadre du traitement de [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Paramètres

*seltyp seltyp*<br/>
Le type de sélection. Les valeurs de type sélection sont décrites dans la section Remarques.

*lpoleobj lpoleobj*<br/>
Pointeur `OLEOBJECT` vers une structure spécifiant le premier objet OLE sélectionné si la sélection contient un ou plusieurs éléments OLE. Si la sélection ne contient pas d’éléments, *lpoleobj* est NULL. La `OLEOBJECT` structure tient un pointeur à un objet OLE v-table.

*lpchrg lpchrg*<br/>
Pointeur vers une structure [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) contenant la sélection actuelle.

### <a name="return-value"></a>Valeur de retour

Gérer le menu contextuelle.

### <a name="remarks"></a>Notes

Cette fonction est une partie typique du traitement vers le bas de bouton de souris droite.

Le type de sélection peut être n’importe quelle combinaison des drapeaux suivants :

- SEL_EMPTY indique qu’il n’y a pas de sélection actuelle.

- SEL_TEXT indique que la sélection actuelle contient du texte.

- SEL_OBJECT indique que la sélection actuelle contient au moins un élément OLE.

- SEL_MULTICHAR indique que la sélection actuelle contient plus d’un caractère de texte.

- SEL_MULTIOBJECT indique que la sélection actuelle contient plus d’un objet OLE.

La mise en œuvre par défaut renvoie NULL. C’est un avancé primordial.

Pour plus d’informations, voir [IRichEditOleCallback:GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) et [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) dans le Windows SDK.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>CRichEditView::GetDocument

Appelez cette fonction pour obtenir `CRichEditDoc` un pointeur à l’associé à cette vue.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) associé à votre `CRichEditView` objet.

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem

Appelez cette fonction pour obtenir l’élément OLE `CRichEditView` qui est actuellement activé en place dans cet objet.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) actif unique dans cette riche vue d’édition ; NULL s’il n’y a pas d’élément OLE actuellement dans l’état actif sur place.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>CRichEditView::GetMargins

Appelez cette fonction pour récupérer les marges actuelles utilisées dans l’impression.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Valeur de retour

Les marges utilisées dans l’impression, mesurées en MM_TWIPS.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>CRichEditView::GetPageRect

Appelez cette fonction pour obtenir les dimensions de la page utilisée dans l’impression.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Valeur de retour

Les limites de la page utilisée dans l’impression, mesurées en MM_TWIPS.

### <a name="remarks"></a>Notes

Cette valeur est basée sur la taille du papier.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>CRichEditView::GetPaperSize

Appelez cette fonction pour récupérer la taille actuelle du papier.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille du papier utilisé dans l’impression, mesurée en MM_TWIPS.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection

Appelez cette fonction pour obtenir les attributs de formatage de paragraphe de la sélection actuelle.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Valeur de retour

Une structure [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) qui contient les attributs de formatage des paragraphes de la sélection actuelle.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) message et la structure [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) dans le SDK Windows.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>CRichEditView::GetPrintRect

Appelez cette fonction pour récupérer les limites de la zone d’impression dans le rectangle de la page.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Valeur de retour

Les limites de la zone d’image utilisée dans l’impression, mesurées en MM_TWIPS.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>CRichEditView::GetPrintWidth

Appelez cette fonction pour déterminer la largeur de la zone d’impression.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la zone d’impression, mesurée en MM_TWIPS.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>CRichEditView::GetRichEditCtrl

Appelez cette fonction pour récupérer l’objet [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) associé à l’objet. `CRichEditView`

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

L’objet `CRichEditCtrl` pour cette vue.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>CRichEditView::GetSelectedItem

Appelez cette fonction pour récupérer l’élément OL (un `CRichEditCntrItem` objet) actuellement sélectionné dans cet `CRichEditView` objet.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) sélectionné dans l’objet; `CRichEditView` NULL si aucun élément n’est sélectionné dans cette vue.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>CRichEditView::GetTextLength

Appelez cette fonction pour récupérer la `CRichEditView` longueur du texte dans cet objet.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du texte `CRichEditView` dans cet objet.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx

Appelez cette fonction de membre pour calculer `CRichEditView` la longueur du texte dans cet objet.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Valeur spécifiant la méthode à utiliser pour déterminer la longueur du texte. Ce membre peut être une ou plusieurs des valeurs énumérées dans le membre des drapeaux de [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) décrit dans le SDK Windows.

*uCodePage*<br/>
Page de code pour la traduction (CP_ACP pour la page de code ANSI, 1200 pour Unicode).

### <a name="return-value"></a>Valeur de retour

Nombre de caractères ou d’octets dans le contrôle de modification. Si des drapeaux incompatibles ont été placés dans *dwFlags*, cette fonction membre retourne E_INVALIDARG.

### <a name="remarks"></a>Notes

`GetTextLengthEx`fournit des moyens supplémentaires de déterminer la durée du texte. Il prend en charge la fonctionnalité Rich Edit 2.0. Pour plus d’informations, voir [à propos des contrôles d’édition riches](/windows/win32/Controls/about-rich-edit-controls) dans le SDK Windows.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject

Appelez cette fonction pour insérer le fichier spécifié (comme un objet [CRichEditCntrItem)](../../mfc/reference/cricheditcntritem-class.md) dans une vue de modification riche.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Chaîne contenant le nom du fichier à insérer.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>CRichEditView::InsertItem

Appelez cette fonction pour insérer un objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) dans une vue d’édition riche.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem (en)*<br/>
Pointeur sur l’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT indiquant le succès de l’insertion.

### <a name="remarks"></a>Notes

Pour plus d’informations sur HRESULT, voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) in the Windows SDK.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>CRichEditView::IsRichEditFormat

Appelez cette fonction pour déterminer si *cf* est un format Clipboard qui est le texte, le texte riche, ou le texte riche avec des éléments OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Paramètres

*Cf*<br/>
Le format Clipboard d’intérêt.

### <a name="return-value"></a>Valeur de retour

Nonzero si *cf* est un format riche de montage ou de texte Clipboard.

## <a name="cricheditviewisselected"></a><a name="isselected"></a>CRichEditView::Isselected

Appelez cette fonction pour déterminer si l’élément OLE spécifié est actuellement sélectionné dans cette vue.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Paramètres

*pDocItem (en)*<br/>
Pointeur vers un objet dans la vue.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’objet est sélectionné; sinon 0.

### <a name="remarks"></a>Notes

Remplacer cette fonction si votre classe de vue dérivée a une méthode différente pour la sélection de manutention des éléments OLE.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent

L’indentation des objets de balle dans une liste; par défaut, 720 unités, soit 1/2 pouce.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap

Indique le type d’enveloppe de mot pour cette vue d’édition riche.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Notes

L’une des valeurs suivantes :

- `WrapNone`Indique aucun emballage automatique de mot.

- `WrapToWindow`Indique l’emballage des mots en fonction de la largeur de la fenêtre.

- `WrapToTargetDevice`Indique l’emballage des mots en fonction des caractéristiques de l’appareil cible.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::WrapChanged](#wrapchanged).

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>CRichEditView::SurCharEffect

Appelez cette fonction pour basculer les effets de formatage des personnages pour la sélection actuelle.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Paramètres

*dwMask*<br/>
Les effets de formatage des personnages à modifier dans la sélection actuelle.

*dwEffect*<br/>
La liste souhaitée des effets de formatage de caractères à basculer.

### <a name="remarks"></a>Notes

Chaque appel à cette fonction agite les effets de formatage spécifiés pour la sélection actuelle.

Pour plus d’informations sur les paramètres *dwMask* et *dwEffect* et leurs valeurs potentielles, consultez les données correspondantes de [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>CRichEditView::OnFindNext

Appelé par le cadre lors du traitement des commandes à partir de la boîte de dialogue Find/Replace.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Chaîne à rechercher.

*bNext (en)*<br/>
La direction à rechercher: TRUE indique vers le bas; FALSE, en haut.

*bCase*<br/>
Indique si la recherche doit être sensible au cas.

*bWord (en)*<br/>
Indique si la recherche est de faire correspondre des mots entiers seulement ou non.

### <a name="remarks"></a>Notes

Appelez cette fonction pour `CRichEditView`trouver du texte dans le . Remplacer cette fonction pour modifier les caractéristiques de recherche de votre classe de vue dérivée.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate

Appelé par le cadre après la vue est d’abord attaché au document, mais avant que la vue est initialement affichée.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction appelle la fonction de membre [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) sans aucune information d’indice (c’est-à-dire en utilisant les valeurs par défaut de 0 pour le paramètre *lHint* et NULL pour le paramètre *pHint).* Remplacer cette fonction pour effectuer une initialisation ponctuelle qui nécessite des informations sur le document. Par exemple, si votre application a des documents de taille fixe, vous pouvez utiliser cette fonction pour initialiser les limites de défilement d’une vue en fonction de la taille du document. Si votre application prend en `OnUpdate` charge des documents de taille variable, utilisez-le pour mettre à jour les limites de défilement chaque fois que le document change.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView:m_nWordWrap](#m_nwordwrap).

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject

Utilisez cette fonction pour charger des données natives à partir d’un élément intégré.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Paramètres

*lpStg (lpStg)*<br/>
Pointeur vers un objet [IStorage.](/windows/win32/api/objidl/nn-objidl-istorage)

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; autrement, 0;

### <a name="remarks"></a>Notes

Typiquement, vous feriez cela en créant un [COleStreamFile](../../mfc/reference/colestreamfile-class.md) autour de la `IStorage`. Le `COleStreamFile` peut être attaché à une archive et [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) appelé pour charger les données.

C’est un avancé primordial.

Pour plus d’informations, voir [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) dans le SDK Windows.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>CRichEditView::OnParaAlign

Appelez cette fonction pour modifier l’alignement du paragraphe pour les paragraphes sélectionnés.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Paramètres

*wAlign (en)*<br/>
Alignement de paragraphe souhaité. L’une des valeurs suivantes :

- PFA_LEFT Aligner les paragraphes avec la marge gauche.

- PFA_RIGHT Aligner les paragraphes avec la bonne marge.

- PFA_CENTER Centre les paragraphes entre les marges.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>CRichEditView::OnPrinterChanged

Remplacer cette fonction pour modifier les caractéristiques de cette vue d’édition riche lorsque l’imprimante change.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Paramètres

*DcPrinter (en)*<br/>
Un objet [CDC](../../mfc/reference/cdc-class.md) pour la nouvelle imprimante.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit la taille du papier à la hauteur physique et la largeur du périphérique de sortie (imprimante). S’il n’y a pas de contexte d’appareil associé à *dcPrinter*, l’implémentation par défaut fixe la taille du papier à 8,5 par 11 pouces.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>CRichEditView::OnReplaceAll

Appelé par le cadre lors du traitement Remplacer toutes les commandes de la boîte de dialogue Replace.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à remplacer.

*lpszReplace*<br/>
Texte de remplacement.

*bCase*<br/>
Indique si la recherche est sensible aux cas.

*bWord (en)*<br/>
Indique si la recherche doit sélectionner des mots entiers ou non.

### <a name="remarks"></a>Notes

Appelez cette fonction pour remplacer tous les occurrences d’un texte donné par une autre chaîne. Remplacer cette fonction pour modifier les caractéristiques de recherche de cette vue.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::FindText](#findtext).

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>CRichEditView::OnReplaceSel

Appelé par le cadre lors du traitement Remplacer les commandes de la boîte de dialogue Replace.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte à remplacer.

*bNext (en)*<br/>
Indique la direction de la recherche: TRUE est en baisse; FALSE, en haut.

*bCase*<br/>
Indique si la recherche est sensible aux cas.

*bWord (en)*<br/>
Indique si la recherche doit sélectionner des mots entiers ou non.

*lpszReplace*<br/>
Texte de remplacement.

### <a name="remarks"></a>Notes

Appelez cette fonction pour remplacer une occurrence d’un texte donné par une autre chaîne. Remplacer cette fonction pour modifier les caractéristiques de recherche de cette vue.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>CRichEditView::OnTextNotFound

Appelé par le cadre chaque fois qu’une recherche échoue.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte qui n’a pas été trouvé.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour modifier la notification de sortie d’un [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Pour plus d’informations, voir [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) dans windows SDK.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect

Le cadre appelle cette fonction pour mettre à jour l’interface utilisateur de commande pour les commandes d’effet de caractère.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Pointeur vers un objet [CCmdUI.](../../mfc/reference/ccmdui-class.md)

*dwMask*<br/>
Indique le masque de formatage des personnages.

*dwEffect*<br/>
Indique l’effet de formatage des personnages.

### <a name="remarks"></a>Notes

Le *masque dwMask* précise quels attributs de formatage de caractère à vérifier. Les drapeaux *dwEffect* listent les attributs de formatage des personnages à définir/effacer.

Pour plus d’informations sur les paramètres *dwMask* et *dwEffect* et leurs valeurs potentielles, consultez les données correspondantes de [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>CRichEditView::OnUpdateParaAlign

Le cadre appelle cette fonction à mettre à jour l’interface utilisateur de commande pour les commandes d’effet de paragraphe.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Paramètres

*pCmdUI (en)*<br/>
Pointeur vers un objet [CCmdUI.](../../mfc/reference/ccmdui-class.md)

*wAlign (en)*<br/>
L’alignement du paragraphe à vérifier. L’une des valeurs suivantes :

- PFA_LEFT Aligner les paragraphes avec la marge gauche.

- PFA_RIGHT Aligner les paragraphes avec la bonne marge.

- PFA_CENTER Centre les paragraphes entre les marges.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>CRichEditView::PrintInsideRect

Appelez cette fonction pour formater une gamme de texte dans un contrôle d’édition riche pour s’adapter à *rectLayout* pour l’appareil spécifié par *pDC*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers un contexte d’appareil pour la zone de sortie.

*rectLayout (rectLayout)*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) qui définit la zone de sortie.

*nIndexStart*<br/>
Index zéro du premier personnage à être formaté.

*nIndexStop*<br/>
Index zéro du dernier personnage à formater.

*bOutput (en)*<br/>
Indique si le texte doit être rendu. Si FALSE, le texte est juste mesuré.

### <a name="return-value"></a>Valeur de retour

L’index du dernier caractère qui s’inscrit dans la zone de sortie plus un.

### <a name="remarks"></a>Notes

Typiquement, cet appel est suivi d’un appel à [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) qui génère la sortie.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>CRichEditView::PrintPage

Appelez cette fonction pour formater une gamme de texte dans un contrôle de modification riche pour le périphérique de sortie spécifié par *pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers un contexte d’appareil pour la sortie de la page.

*nIndexStart*<br/>
Index zéro du premier personnage à être formaté.

*nIndexStop*<br/>
Index zéro du dernier personnage à formater.

### <a name="return-value"></a>Valeur de retour

L’index du dernier personnage qui s’adapte sur la page plus un.

### <a name="remarks"></a>Notes

La mise en page de chaque page est contrôlée par [GetPageRect](#getpagerect) et [GetPrintRect](#getprintrect). Typiquement, cet appel est suivi d’un appel à [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) qui génère la sortie.

Notez que les marges sont relatives à la page physique, pas la page logique. Ainsi, les marges de zéro vont souvent couper le texte puisque de nombreuses imprimantes ont des zones imprimables sur la page. Pour éviter de couper votre texte, vous devez appeler [SetMargins](#setmargins) et définir des marges raisonnables avant l’impression.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>CRichEditView::QueryAcceptData

Appelé par le cadre à coller un objet dans le montage riche.

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>Paramètres

*lpdataobj*<br/>
Pointeur à [l’IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) à la requête.

*lpcfFormat*<br/>
Pointeur vers le format de données acceptable.

*dwReco*<br/>
Non utilisé.

*bRéally*<br/>
Indique si l’opération de pâte doit se poursuivre ou non.

*hMetaFile (en)*<br/>
Une poignée au metafile utilisé pour dessiner l’icône de l’élément.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT signalant le succès de l’opération.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour gérer différentes organisations d’éléments COM dans votre classe de documents dérivée. C’est un avancé primordial.

Pour plus d’informations `IDataObject`sur HRESULT et , voir [Structure of COM Error Codes](/windows/win32/com/structure-of-com-error-codes) et [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), respectivement, dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>CRichEditView::SetCharFormat

Appelez cette fonction pour définir les attributs de `CRichEditView` formatage de caractère pour le nouveau texte dans cet objet.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Paramètres

*Cf*<br/>
[Structure CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) contenant les nouveaux attributs de formatage de caractères par défaut.

### <a name="remarks"></a>Notes

Seuls les attributs `dwMask` spécifiés par le membre de *cf* sont modifiés par cette fonction.

Pour plus d’informations, voir [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) message et la structure [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>CRichEditView::SetMargins

Appelez cette fonction pour définir les marges d’impression pour cette vue d’édition riche.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Paramètres

*rectMargin*<br/>
Les nouvelles valeurs de marge pour l’impression, mesurées en MM_TWIPS.

### <a name="remarks"></a>Notes

Si [m_nWordWrap](#m_nwordwrap) est, `WrapToTargetDevice`vous devez appeler [WrapChanged](#wrapchanged) après avoir utilisé cette fonction pour ajuster les caractéristiques d’impression.

Notez que les marges utilisées par [PrintPage](#printpage) sont relatives à la page physique, et non à la page logique. Ainsi, les marges de zéro vont souvent couper le texte puisque de nombreuses imprimantes ont des zones imprimables sur la page. Pour éviter de couper votre texte, vous devriez appeler l’utilisation `SetMargins` pour définir les marges raisonnables de l’imprimante avant l’impression.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>CRichEditView::SetPaperSize

Appelez cette fonction pour définir la taille du papier pour l’impression de cette vue d’édition riche.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Paramètres

*sizePaper*<br/>
Les nouvelles valeurs de taille de papier pour l’impression, mesurées en MM_TWIPS.

### <a name="remarks"></a>Notes

Si [m_nWordWrap](#m_nwordwrap) est, `WrapToTargetDevice`vous devez appeler [WrapChanged](#wrapchanged) après avoir utilisé cette fonction pour ajuster les caractéristiques d’impression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>CRichEditView::SetParaFormat

Appelez cette fonction pour définir les attributs de `CRichEditView` formatage de paragraphe pour la sélection actuelle dans cet objet.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Paramètres

*Pf*<br/>
[Structure PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) contenant les nouveaux attributs de formatage de paragraphe par défaut.

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; autrement, 0.

### <a name="remarks"></a>Notes

Seuls les attributs `dwMask` spécifiés par le membre de *pf* sont modifiés par cette fonction.

Pour plus d’informations, voir [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) message et la structure [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>CRichEditView::TextNotFound

Appelez cette fonction pour réinitialiser l’état de recherche interne du contrôle [CRichEditView](../../mfc/reference/cricheditview-class.md) après un appel raté à [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Contient la chaîne de texte qui n’a pas été trouvée.

### <a name="remarks"></a>Notes

Il est recommandé que cette méthode soit appelée immédiatement après les appels ratés à [FindText](#findtext) afin que l’état de recherche interne du contrôle soit correctement réinitialisé.

Le paramètre *lpszFind* doit inclure le même contenu que la chaîne fournie à [FindText](#findtext). Après avoir réinitialisé l’état de recherche interne, cette méthode appellera la méthode [OnTextNotFound](#ontextnotfound) avec la chaîne de recherche fournie.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CRichEditView::FindText](#findtext).

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>CRichEditView::WrapChanged

Appelez cette fonction lorsque les caractéristiques d’impression ont changé ( [SetMargins](#setmargins) ou [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Notes

Remplacer cette fonction pour modifier la façon dont la vue d’édition riche répond aux changements dans [m_nWordWrap](#m_nwordwrap) ou les caractéristiques d’impression ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[Échantillon MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc, classe](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem, classe](../../mfc/reference/cricheditcntritem-class.md)
