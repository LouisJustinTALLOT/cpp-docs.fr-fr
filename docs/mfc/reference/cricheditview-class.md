---
title: CRichEditView (classe)
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
ms.openlocfilehash: 8cfaef2c8b064cb9faa8c0f6bf65a8868eed7cc7
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178738"
---
# <a name="cricheditview-class"></a>CRichEditView (classe)

Avec [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) et [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte de l’architecture document / vue de MFC.

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
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Déplace une boîte de dialogue afin qu’il ne masque la sélection actuelle.|
|[CRichEditView::CanPaste](#canpaste)|Indique si le Presse-papiers contient des données qui peuvent être collées dans la vue RichEdit.|
|[CRichEditView::DoPaste](#dopaste)|Colle un élément OLE dans cette vue RichEdit.|
|[CRichEditView::FindText](#findtext)|Recherche le texte spécifié, en appelant le curseur d’attente.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Recherche le texte spécifié.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Récupère le caractère de mise en forme d’attributs pour la sélection actuelle.|
|[CRichEditView::GetDocument](#getdocument)|Récupère un pointeur vers le connexes [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Récupère l’élément OLE qui est actif actuellement en place dans la vue RichEdit.|
|[CRichEditView::GetMargins](#getmargins)|Récupère les marges pour cette vue RichEdit.|
|[CRichEditView::GetPageRect](#getpagerect)|Récupère le rectangle de page pour cette vue RichEdit.|
|[CRichEditView::GetPaperSize](#getpapersize)|Récupère la taille du papier pour cette vue RichEdit.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Récupère le paragraphe mise en forme d’attributs pour la sélection actuelle.|
|[CRichEditView::GetPrintRect](#getprintrect)|Récupère le rectangle d’impression pour cette vue RichEdit.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Récupère la largeur d’impression pour cette vue RichEdit.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Récupère le contrôle RichEdit.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Récupère l’élément sélectionné à partir de la vue RichEdit.|
|[CRichEditView::GetTextLength](#gettextlength)|Récupère la longueur du texte dans la vue RichEdit.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Récupère le nombre de caractères ou d’octets dans la vue RichEdit. Liste d’indicateurs développée pour une méthode permettant de déterminer la longueur.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Insère un fichier sous la forme d’un élément OLE.|
|[CRichEditView::InsertItem](#insertitem)|Insère un nouvel élément sous la forme d’un élément OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Indique si le Presse-papiers contient des données dans un format texte ou RTF.|
|[CRichEditView::OnCharEffect](#onchareffect)|Active ou désactive le caractère de mise en forme pour la sélection actuelle.|
|[CRichEditView::OnParaAlign](#onparaalign)|Modifie l’alignement des paragraphes.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Met à jour l’interface utilisateur de commande pour les fonctions membres publiques de caractère.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Met à jour l’interface utilisateur de commande pour les fonctions membres publiques de paragraphe.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Met en forme le texte spécifié dans le rectangle donné.|
|[CRichEditView::PrintPage](#printpage)|Met en forme le texte spécifié dans la page donnée.|
|[CRichEditView::SetCharFormat](#setcharformat)|Définit le caractère de mise en forme d’attributs pour la sélection actuelle.|
|[CRichEditView::SetMargins](#setmargins)|Définit les marges de cette riche modifier la vue.|
|[CRichEditView::SetPaperSize](#setpapersize)|Définit le format du papier pour cette vue RichEdit.|
|[CRichEditView::SetParaFormat](#setparaformat)|Définit le paragraphe mise en forme d’attributs pour la sélection actuelle.|
|[CRichEditView::TextNotFound](#textnotfound)|Réinitialise l’état de la recherche interne du contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Récupère un objet Clipboard pour une plage dans cette vue RichEdit.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Récupère un menu contextuel à utiliser sur un bouton de souris droit vers le bas.|
|[CRichEditView::IsSelected](#isselected)|Indique si l’élément OLE donné est sélectionné ou non.|
|[CRichEditView::OnFindNext](#onfindnext)|Recherche l’occurrence suivante d’une sous-chaîne.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Actualise une vue lorsque c’est le premier joint à un document.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Extrait les données natives à partir d’un élément OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Définit les caractéristiques d’impression pour le périphérique donné.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Remplace toutes les occurrences d’une chaîne donnée par une nouvelle chaîne.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Remplace la sélection actuelle.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Gère les notifications d’utilisateur que le texte demandé est introuvable.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Requêtes à visualiser concernant les données sur le `IDataObject`.|
|[CRichEditView::WrapChanged](#wrapchanged)|Ajuste le périphérique de sortie cible pour cette vue, selon la valeur de RichEdit `m_nWordWrap`.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Indique la quantité de mise en retrait pour les listes à puces.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Indique les contraintes de type wrap de word.|

## <a name="remarks"></a>Notes

Un « contrôle RichEdit » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte peut avoir de caractère et de mise en forme de paragraphe et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour la mise en forme de texte. Toutefois, une application doit implémenter les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles à l’utilisateur.

`CRichEditView` gère le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` gère la liste des éléments de client OLE qui se trouvent dans la vue. `CRichEditCntrItem` fournit l’accès côté conteneur à l’élément client OLE.

Ce contrôle commun de Windows (et par conséquent le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes associées) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT versions 3.51 et ultérieures.

Pour obtenir un exemple d’utilisation d’une vue RichEdit dans une application MFC, consultez le [WORDPAD](../../visual-cpp-samples.md) exemple d’application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrich.h

##  <a name="adjustdialogposition"></a>  CRichEditView::AdjustDialogPosition

Appelez cette fonction pour déplacer la boîte de dialogue donné afin qu’il ne masque pas la sélection actuelle.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Paramètres

*pDlg*<br/>
Pointeur vers un `CDialog` objet.

##  <a name="canpaste"></a>  CRichEditView::CanPaste

Appelez cette fonction pour déterminer si le Presse-papiers contient des informations qui peuvent être collées dans cette vue RichEdit.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le Presse-papiers contient des données dans un format qui peut accepter de cette vue RichEdit ; Sinon, 0.

##  <a name="cricheditview"></a>  CRichEditView::CRichEditView

Appelez cette fonction pour créer un `CRichEditView` objet.

```
CRichEditView();
```

##  <a name="dopaste"></a>  CRichEditView::DoPaste

Appelez cette fonction pour coller l’élément OLE dans *dataobj* dans ce document/vue d’édition enrichie.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Paramètres

*dataobj*<br/>
Le [COleDataObject](../../mfc/reference/coledataobject-class.md) contenant les données à coller.

*CF*<br/>
Le format de Presse-papiers souhaité.

*hMetaPict*<br/>
Métafichier qui représente l’élément à coller.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction dans le cadre de l’implémentation par défaut de [QueryAcceptData](#queryacceptdata).

Cette fonction détermine le type de collage en fonction des résultats du Gestionnaire de collage spécial. Si *cf* est 0, le nouvel élément utilise la représentation sous forme d’icône actuelle. Si *cf* est différent de zéro et *hMetaPict* n’est pas NULL, le nouvel élément utilise *hMetaPict* pour sa représentation sous forme.

##  <a name="findtext"></a>  CRichEditView::FindText

Appelez cette fonction pour rechercher le texte spécifié et définissez comme étant la sélection actuelle.

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
Indique si la recherche respecte la casse.

*bWord*<br/>
Indique si la recherche doit correspondre à des mots entiers uniquement, pas les parties de mots.

*bsuivant*<br/>
Indique la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSE, le sens de la recherche est vers le début de la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le *lpszFind* texte est trouvé ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction affiche le curseur d’attente pendant l’opération de recherche.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>  CRichEditView::FindTextSimple

Appelez cette fonction pour rechercher le texte spécifié et définissez comme étant la sélection actuelle.

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
Indique si la recherche respecte la casse.

*bWord*<br/>
Indique si la recherche doit correspondre à des mots entiers uniquement, pas les parties de mots.

*bsuivant*<br/>
Indique la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSE, le sens de la recherche est vers le début de la mémoire tampon.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le *lpszFind* texte est trouvé ; sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::FindText](#findtext).

##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection

Appelez cette fonction pour obtenir le caractère de mise en forme des attributs de la sélection actuelle.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Valeur de retour

Un [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) structure qui contient le caractère de mise en forme des attributs de la sélection actuelle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le [EM_GETCHARFORMAT](/windows/desktop/Controls/em-getcharformat) message et le [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) structure dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData

L’infrastructure appelle cette fonction dans le cadre du traitement de [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Paramètres

*lpchrg*<br/>
Pointeur vers le [structure CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) structure qui spécifie la plage de caractères (et les éléments OLE) pour copier l’objet de données spécifié par *lplpdataobj*.

*dwReco*<br/>
Indicateur d’opération du Presse-papiers. Peut prendre l’une des valeurs suivantes.

- Copie RECO_COPY dans le Presse-papiers.

- RECO_CUT Couper vers le Presse-papiers.

- Faites glisser RECO_DRAG opération (glisser -déplacer).

- Opération Supprimer RECO_DROP (glisser -déplacer).

- RECO_PASTE les coller à partir du Presse-papiers.

*lpRichDataObj*<br/>
Pointeur vers un [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) objet contenant les données du Presse-papiers à partir de la riche contrôle d’édition ( [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Pointeur vers la variable pointeur qui reçoit l’adresse de la `IDataObject` objet représentant la plage spécifiée dans le *lpchrg* paramètre. La valeur de *lplpdataobj* est ignoré si une erreur est retournée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT la réussite de l’opération de création de rapports. Pour plus d’informations sur le HRESULT, consultez [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) dans le SDK Windows.

### <a name="remarks"></a>Notes

Si la valeur de retour indique la réussite, `IRichEditOleCallback::GetClipboardData` retourne le `IDataObject` accessible par *lplpdataobj*; sinon, elle retourne l’accessibles par *lpRichDataObj*. Remplacez cette fonction pour fournir vos propres données du Presse-papiers. L’implémentation par défaut de cette fonction retourne E_NOTIMPL.

Il s’agit d’une avancée substituable.

Pour plus d’informations, consultez [IRichEditOle::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getclipboarddata), et [structure CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) dans le Kit de développement logiciel Windows et consultez [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) dans le Kit de développement logiciel Windows.

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

L’infrastructure appelle cette fonction dans le cadre du traitement de [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Paramètres

*seltyp*<br/>
Le type de sélection. Les valeurs de type de sélection sont décrits dans la section Notes.

*lpoleobj*<br/>
Pointeur vers un `OLEOBJECT` structure spécifiant le premier objet OLE sélectionné si la sélection contient un ou plusieurs éléments OLE. Si la sélection ne contient aucun élément, *lpoleobj* a la valeur NULL. Le `OLEOBJECT` structure conserve un pointeur vers une objet OLE v-table.

*lpchrg*<br/>
Pointeur vers un [structure CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) structure contenant la sélection actuelle.

### <a name="return-value"></a>Valeur de retour

Handle vers le menu contextuel.

### <a name="remarks"></a>Notes

Cette fonction est une partie standard du bouton droit de la souris vers le bas de traitement.

Le type de sélection peut être n’importe quelle combinaison des indicateurs suivants :

- SEL_EMPTY indique qu’il n’existe pas de sélection.

- SEL_TEXT indique que la sélection actuelle contienne du texte.

- SEL_OBJECT indique que la sélection actuelle contienne au moins un élément OLE.

- SEL_MULTICHAR indique que la sélection actuelle contienne plusieurs caractères de texte.

- SEL_MULTIOBJECT indique que la sélection actuelle contienne plus d’un objet OLE.

L’implémentation par défaut retourne la valeur NULL. Il s’agit d’une avancée substituable.

Pour plus d’informations, consultez [IRichEditOleCallback::GetContextMenu](/windows/desktop/api/richole/nf-richole-iricheditolecallback-getcontextmenu) et [structure CHARRANGE](/windows/desktop/api/richedit/ns-richedit-_charrange) dans le SDK Windows.

##  <a name="getdocument"></a>  CRichEditView::GetDocument

Appelez cette fonction pour obtenir un pointeur vers le `CRichEditDoc` associé à cette vue.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) objet associé à votre `CRichEditView` objet.

##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem

Appel de cette fonction pour obtenir le OLE d’élément qui est actuellement activé sur place dans cette `CRichEditView` objet.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers l’actif unique, sur place [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objet dans cette vue RichEdit ; NULL s’il n’existe actuellement aucun élément OLE dans un état actif sur place.

##  <a name="getmargins"></a>  CRichEditView::GetMargins

Appelez cette fonction pour récupérer les marges actuels utilisés pour l’impression.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Valeur de retour

Les marges utilisés à l’impression, mesurée en MM_TWIPS.

##  <a name="getpagerect"></a>  CRichEditView::GetPageRect

Appelez cette fonction pour obtenir les dimensions de la page utilisée dans l’impression.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Valeur de retour

Les limites de la page utilisée dans l’impression, mesurée en MM_TWIPS.

### <a name="remarks"></a>Notes

Cette valeur est basée sur le format du papier.

##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize

Appelez cette fonction pour récupérer la taille du papier.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valeur de retour

La taille du papier utilisé pour l’impression, mesurée en MM_TWIPS.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection

Appelez cette fonction pour obtenir le paragraphe mise en forme des attributs de la sélection actuelle.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Valeur de retour

Un [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) structure qui contient le paragraphe mise en forme des attributs de la sélection actuelle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EM_GETPARAFORMAT](/windows/desktop/Controls/em-getparaformat) message et [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) structure dans le SDK Windows.

##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect

Appelez cette fonction pour récupérer les limites de la zone d’impression dans le rectangle de la page.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Valeur de retour

Les limites de la zone d’image utilisés dans l’impression, mesurée en MM_TWIPS.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth

Appelez cette fonction pour déterminer la largeur de la zone d’impression.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Valeur de retour

La largeur de la zone d’impression, mesurée en MM_TWIPS.

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

Appelez cette fonction pour récupérer le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) objet associé à la `CRichEditView` objet.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Le `CRichEditCtrl` objet pour cette vue.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::FindText](#findtext).

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

Appelez cette fonction pour récupérer l’élément OLE (un `CRichEditCntrItem` objet) actuellement sélectionné dans ce `CRichEditView` objet.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objet sélectionné dans le `CRichEditView` de l’objet ; NULL si aucun élément n’est sélectionné dans cette vue.

##  <a name="gettextlength"></a>  CRichEditView::GetTextLength

Appelez cette fonction pour récupérer la longueur du texte dans ce `CRichEditView` objet.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Valeur de retour

La longueur du texte dans ce `CRichEditView` objet.

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

Appelez cette fonction membre pour calculer la longueur du texte dans ce `CRichEditView` objet.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Valeur qui spécifie la méthode à utiliser pour déterminer la longueur du texte. Ce membre peut être une ou plusieurs des valeurs répertoriées dans le membre d’indicateurs de [GETTEXTLENGTHEX](/windows/desktop/api/richedit/ns-richedit-_gettextlengthex) décrites dans le SDK Windows.

*uCodePage*<br/>
Page de codes pour la traduction (CP_ACP pour la Page de codes ANSI, 1200 pour Unicode).

### <a name="return-value"></a>Valeur de retour

Le nombre de caractères ou d’octets dans le contrôle d’édition. Si les indicateurs incompatibles ont été définis *dwFlags*, cette fonction membre retourne E_INVALIDARG.

### <a name="remarks"></a>Notes

`GetTextLengthEx` Fournit des méthodes supplémentaires permettant de déterminer la longueur du texte. Il prend en charge la fonctionnalité Rich Edit 2.0. Pour plus d’informations, consultez [sur les contrôles RichEdit](/windows/desktop/Controls/about-rich-edit-controls) dans le SDK Windows.

##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject

Appelez cette fonction pour insérer le fichier spécifié (comme un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objet) dans une riche modifier la vue.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Chaîne contenant le nom du fichier à insérer.

##  <a name="insertitem"></a>  CRichEditView::InsertItem

Appelez cette fonction pour insérer un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objet dans une vue RichEdit.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément à insérer.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT indiquant la réussite de l’insertion.

### <a name="remarks"></a>Notes

Pour plus d’informations sur le HRESULT, consultez [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) dans le SDK Windows.

##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat

Appelez cette fonction pour déterminer si *cf* est un format de Presse-papiers qui est le texte, texte enrichi ou texte enrichi avec les éléments OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Paramètres

*CF*<br/>
Le format Presse-papiers pertinent.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si *cf* est un format de Presse-papiers de modifier ou de texte enrichi.

##  <a name="isselected"></a>  CRichEditView::IsSelected

Appelez cette fonction pour déterminer si l’élément OLE spécifié est actuellement sélectionné dans cette vue.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Paramètres

*pDocItem*<br/>
Pointeur vers un objet dans la vue.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet est sélectionné ; sinon 0.

### <a name="remarks"></a>Notes

Remplacez cette fonction si votre classe d’affichage dérivée a une autre méthode pour gérer la sélection d’éléments OLE.

##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent

La mise en retrait pour les éléments de liste à puces dans une liste ; par défaut, les 720 unités, c'est-à-dire 1/2 pouce.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

Indique le type de retour pour cette vue RichEdit.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Notes

Une des valeurs suivantes :

- `WrapNone` N’indique aucun déplacement automatique des mots.

- `WrapToWindow` Indique le retour automatique en fonction de la largeur de la fenêtre.

- `WrapToTargetDevice` Indique le retour automatique en fonction des caractéristiques de l’appareil cible.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::WrapChanged](#wrapchanged).

##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect

Appelez cette fonction pour activer/désactiver le caractère de mise en forme des effets de la sélection actuelle.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Paramètres

*dwMask*<br/>
Le caractère de mise en forme des effets à modifier dans la sélection actuelle.

*dwEffect*<br/>
La liste souhaitée des effets pour activer/désactiver la mise en forme de caractère.

### <a name="remarks"></a>Notes

Chaque appel à cette fonction active ou désactive les effets de mise en forme spécifiées pour la sélection actuelle.

Pour plus d’informations sur la *dwMask* et *dwEffect* paramètres et leurs valeurs potentielles, consultez les membres de données correspondants de [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>  CRichEditView::OnFindNext

Appelé par l’infrastructure lors du traitement des commandes à partir de la boîte de dialogue Rechercher/Remplacer.

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

*bsuivant*<br/>
La direction à rechercher : TRUE indique que le bas ; FALSE, le haut.

*bCase*<br/>
Indique si la recherche doit respecter la casse.

*bWord*<br/>
Indique si la recherche doit correspondre à des mots entiers uniquement ou non.

### <a name="remarks"></a>Notes

Appelez cette fonction pour rechercher du texte dans le `CRichEditView`. Remplacez cette fonction pour modifier les caractéristiques de recherche pour votre classe d’affichage dérivé.

##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate

Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle le [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) fonction membre sans aucune information d’indicateur (autrement dit, en utilisant les valeurs par défaut de 0 pour le *lHint* paramètre et NULL pour le *pHint* paramètre). Remplacez cette fonction pour effectuer toute initialisation à usage unique qui requiert des informations sur le document. Par exemple, si votre application comporte des documents de taille fixe, vous pouvez utiliser cette fonction pour initialiser les limites de défilement de l’affichage en fonction de la taille du document. Si votre application prend en charge les documents de taille variable, utilisez `OnUpdate` pour mettre à jour le défilement limite chaque fois que les modifications de document.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject

Utilisez cette fonction pour charger des données natives à partir d’un élément incorporé.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Paramètres

*lpStg*<br/>
Pointeur vers un [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) objet.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; Sinon, 0 ;

### <a name="remarks"></a>Notes

En règle générale, vous faites cela en créant un [COleStreamFile](../../mfc/reference/colestreamfile-class.md) autour de la `IStorage`. Le `COleStreamFile` peuvent être attachés à une archive et [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) appelée pour charger les données.

Il s’agit d’une avancée substituable.

Pour plus d’informations, consultez [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) dans le SDK Windows.

##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign

Appelez cette fonction pour modifier l’alignement du paragraphe des paragraphes sélectionnés.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Paramètres

*wAlign*<br/>
Alignement du paragraphe souhaité. Une des valeurs suivantes :

- PFA_LEFT aligner les paragraphes avec la marge de gauche.

- PFA_RIGHT aligner les paragraphes avec la marge de droite.

- PFA_CENTER centre les paragraphes entre les marges.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged

Remplacez cette fonction pour changer les caractéristiques de cette vue RichEdit lorsque l’imprimante est modifiée.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Paramètres

*dcPrinter*<br/>
Un [CDC](../../mfc/reference/cdc-class.md) objet pour la nouvelle imprimante.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit le format du papier à la hauteur physique et la largeur du périphérique de sortie (imprimante). S’il existe aucun contexte de périphérique n’associé à *dcPrinter*, l’implémentation par défaut définit le format du papier sur 8,5 par 11 pouces.

##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll

Appelé par l’infrastructure lors du traitement de remplacer toutes les commandes à partir de la boîte de dialogue Remplacer.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte à remplacer.

*lpszReplace*<br/>
Le texte de remplacement.

*bCase*<br/>
Indique si la recherche respecte la casse.

*bWord*<br/>
Indique si la recherche doit sélectionner les mots entiers ou non.

### <a name="remarks"></a>Notes

Appelez cette fonction pour remplacer toutes les occurrences d’un texte donné avec une autre chaîne. Remplacez cette fonction pour modifier les caractéristiques de recherche pour cette vue.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::FindText](#findtext).

##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel

Appelé par l’infrastructure lors du traitement des commandes de remplacement à partir de la boîte de dialogue Remplacer.

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
Texte à remplacer.

*bsuivant*<br/>
Indique la direction de la recherche : La valeur TRUE est arrêté ; FALSE, le haut.

*bCase*<br/>
Indique si la recherche respecte la casse.

*bWord*<br/>
Indique si la recherche doit sélectionner les mots entiers ou non.

*lpszReplace*<br/>
Le texte de remplacement.

### <a name="remarks"></a>Notes

Appelez cette fonction pour remplacer une occurrence d’un texte donné avec une autre chaîne. Remplacez cette fonction pour modifier les caractéristiques de recherche pour cette vue.

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

Appelé par le framework chaque fois qu’une recherche échoue.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Le texte qui est introuvable.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour modifier la notification de sortie à partir d’un [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep).

Pour plus d’informations, consultez [MessageBeep](/windows/desktop/api/winuser/nf-winuser-messagebeep) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect

L’infrastructure appelle cette fonction pour mettre à jour de la commande interface utilisateur pour les commandes d’effet de caractère.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers un [CCmdUI](../../mfc/reference/ccmdui-class.md) objet.

*dwMask*<br/>
Indique le caractère de masque de mise en forme.

*dwEffect*<br/>
Indique le caractère de mise en forme d’effet.

### <a name="remarks"></a>Notes

Le masque *dwMask* Spécifie le caractère de mise en forme d’attributs à vérifier. Les indicateurs *dwEffect* le formatage des attributs à enlever ou supprimer des caractères de la liste.

Pour plus d’informations sur la *dwMask* et *dwEffect* paramètres et leurs valeurs potentielles, consultez les membres de données correspondants de [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign

L’infrastructure appelle cette fonction pour mettre à jour de la commande interface utilisateur pour les commandes d’effet de paragraphe.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers un [CCmdUI](../../mfc/reference/ccmdui-class.md) objet.

*wAlign*<br/>
L’alignement du paragraphe à vérifier. Une des valeurs suivantes :

- PFA_LEFT aligner les paragraphes avec la marge de gauche.

- PFA_RIGHT aligner les paragraphes avec la marge de droite.

- PFA_CENTER centre les paragraphes entre les marges.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect

Appelez cette fonction pour mettre en forme une plage de texte dans un contrôle RichEdit pour s’ajuster au *rectLayout* pour l’appareil spécifié par *pDC*.

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
Pointeur vers un contexte de périphérique pour la zone de sortie.

*rectLayout*<br/>
[RECT](/windows/desktop/api/windef/ns-windef-tagrect) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) qui définit la zone de sortie.

*nIndexStart*<br/>
Index de base zéro du premier caractère à mettre en forme.

*nIndexStop*<br/>
Index de base zéro du dernier caractère à mettre en forme.

*bOutput*<br/>
Indique si le texte doit être restitué. Si la valeur est FALSE, le texte est simplement mesuré.

### <a name="return-value"></a>Valeur de retour

L’index du dernier caractère qui correspond à la zone de sortie, plus un.

### <a name="remarks"></a>Notes

En règle générale, cet appel est suivi par un appel à [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) qui génère la sortie.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::GetPaperSize](#getpapersize).

##  <a name="printpage"></a>  CRichEditView::PrintPage

Appelez cette fonction pour mettre en forme une plage de texte dans un contrôle RichEdit pour le périphérique de sortie spécifié par *pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointeur vers un contexte de périphérique pour la sortie de page.

*nIndexStart*<br/>
Index de base zéro du premier caractère à mettre en forme.

*nIndexStop*<br/>
Index de base zéro du dernier caractère à mettre en forme.

### <a name="return-value"></a>Valeur de retour

L’index du dernier caractère qui tienne sur la page, plus un.

### <a name="remarks"></a>Notes

La disposition de chaque page est contrôlée par [GetPageRect](#getpagerect) et [GetPrintRect](#getprintrect). En règle générale, cet appel est suivi par un appel à [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) qui génère la sortie.

Notez que les marges sont par rapport à la page physique, pas sur la page logique. Par conséquent, les marges de zéro fait correspondre souvent le texte dans la mesure où de nombreuses imprimantes ont des zones non imprimables dans la page. Pour éviter le découpage de votre texte, vous devez appeler [SETMARGINS ne](#setmargins) et définir les marges raisonnables avant l’impression.

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

Appelé par l’infrastructure de coller un objet dans l’édition enrichi.

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
Pointeur vers le [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) à interroger.

*lpcfFormat*<br/>
Pointeur vers le format de données acceptables.

*dwReco*<br/>
Non utilisé.

*bReally*<br/>
Indique si l’opération de collage doit continuer ou non.

*hMetaFile*<br/>
Handle du métafichier utilisé pour dessiner l’icône de l’élément.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT la réussite de l’opération de création de rapports.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour gérer une organisation différente des éléments de COM dans votre classe de document dérivée. Il s’agit d’une avancée substituable.

Pour plus d’informations sur la valeur HRESULT et `IDataObject`, consultez [Structure of COM Error Codes](/windows/desktop/com/structure-of-com-error-codes) et [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject), respectivement, dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat

Appelez cette fonction pour définir le caractère de mise en forme d’attributs pour le nouveau texte dans ce `CRichEditView` objet.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Paramètres

*CF*<br/>
[CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) structure contenant le caractère par défaut nouvelle mise en forme d’attributs.

### <a name="remarks"></a>Notes

Seuls les attributs spécifiés par le `dwMask` membre *cf* sont modifiés par cette fonction.

Pour plus d’informations, consultez [EM_SETCHARFORMAT](/windows/desktop/Controls/em-setcharformat) message et [CHARFORMAT2](/windows/desktop/api/richedit/ns-richedit-charformat2a) structure dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>  CRichEditView::SetMargins

Appelez cette fonction pour définir les marges d’impression pour cette vue RichEdit.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Paramètres

*rectMargin*<br/>
Les nouvelles valeurs de marge pour l’impression, mesurée en MM_TWIPS.

### <a name="remarks"></a>Notes

Si [m_nWordWrap](#m_nwordwrap) est `WrapToTargetDevice`, vous devez appeler [WrapChanged](#wrapchanged) après l’utilisation de cette fonction pour ajuster les caractéristiques d’impression.

Notez que les marges utilisés par [PrintPage](#printpage) sont relatives à la page physique, pas sur la page logique. Par conséquent, les marges de zéro fait correspondre souvent le texte dans la mesure où de nombreuses imprimantes ont des zones non imprimables dans la page. Pour éviter le découpage de votre texte, vous devez appeler utilisez `SetMargins` pour définir les marges d’impression raisonnable avant l’impression.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::GetPaperSize](#getpapersize).

##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize

Appelez cette fonction pour définir le format du papier pour l’impression de cette vue RichEdit.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Paramètres

*sizePaper*<br/>
Les nouvelles valeurs de taille de papier pour l’impression, mesurée en MM_TWIPS.

### <a name="remarks"></a>Notes

Si [m_nWordWrap](#m_nwordwrap) est `WrapToTargetDevice`, vous devez appeler [WrapChanged](#wrapchanged) après l’utilisation de cette fonction pour ajuster les caractéristiques d’impression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat

Appelez cette fonction pour définir le paragraphe mise en forme d’attributs pour la sélection actuelle dans ce `CRichEditView` objet.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Paramètres

*pf*<br/>
[PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) structure contenant la nouvelle valeur par défaut des attributs de mise en forme de paragraphe.

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

Seuls les attributs spécifiés par le `dwMask` membre *pf* sont modifiés par cette fonction.

Pour plus d’informations, consultez [EM_SETPARAFORMAT](/windows/desktop/Controls/em-setparaformat) message et [PARAFORMAT2](/windows/desktop/api/richedit/ns-richedit-paraformat2) structure dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>  CRichEditView::TextNotFound

Appelez cette fonction pour réinitialiser l’état de la recherche interne de la [CRichEditView](../../mfc/reference/cricheditview-class.md) contrôle après l’appel à un échec [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Contient la chaîne de texte qui est introuvable.

### <a name="remarks"></a>Notes

Il est recommandé que cette méthode est appelée immédiatement après les appels en échec pour [FindText](#findtext) afin que l’état de la recherche interne du contrôle est réinitialisé correctement.

Le *lpszFind* paramètre doit inclure le même contenu que la chaîne fournie aux [FindText](#findtext). Après la réinitialisation de l’état de la recherche interne, cette méthode appelle la [OnTextNotFound](#ontextnotfound) méthode avec la chaîne de recherche fourni.

### <a name="example"></a>Exemple

  Consultez l’exemple de [CRichEditView::FindText](#findtext).

##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged

Appelez cette fonction quand les caractéristiques d’impression ont été modifiés ( [SETMARGINS ne](#setmargins) ou [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Notes

Remplacement de cette fonction pour modifier la façon dont la vue RichEdit répond aux modifications dans [m_nWordWrap](#m_nwordwrap) ou les caractéristiques d’impression ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc, classe](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem, classe](../../mfc/reference/cricheditcntritem-class.md)
