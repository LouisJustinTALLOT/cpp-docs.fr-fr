---
description: 'En savoir plus sur : CRichEditView, classe'
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
ms.openlocfilehash: cf5c504058332b652023d746aaadb0c8c80fccce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264763"
---
# <a name="cricheditview-class"></a>CRichEditView (classe)

Avec [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) et [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte de l’architecture d’affichage de document MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRichEditView :: CRichEditView](#cricheditview)|Construit un objet `CRichEditView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRichEditView :: AdjustDialogPosition](#adjustdialogposition)|Déplace une boîte de dialogue pour qu’elle ne masque pas la sélection actuelle.|
|[CRichEditView :: CanPaste](#canpaste)|Indique si le presse-papiers contient des données qui peuvent être collées dans la vue RichEdit.|
|[CRichEditView ::D oPaste](#dopaste)|Colle un élément OLE dans cette vue RichEdit.|
|[CRichEditView :: FindText](#findtext)|Recherche le texte spécifié, en appelant le curseur d’attente.|
|[CRichEditView :: FindTextSimple](#findtextsimple)|Recherche le texte spécifié.|
|[CRichEditView :: GetCharFormatSelection](#getcharformatselection)|Récupère les attributs de mise en forme de caractères pour la sélection actuelle.|
|[CRichEditView :: GetDocument](#getdocument)|Récupère un pointeur vers les [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)connexes.|
|[CRichEditView :: GetInPlaceActiveItem](#getinplaceactiveitem)|Récupère l’élément OLE qui est actuellement actif sur place dans la vue RichEdit.|
|[CRichEditView :: GetMargins](#getmargins)|Récupère les marges pour cette vue RichEdit.|
|[CRichEditView :: GetPageRect](#getpagerect)|Récupère le rectangle de page pour cette vue RichEdit.|
|[CRichEditView :: GetPaperSize](#getpapersize)|Récupère le format du papier pour cette vue RichEdit.|
|[CRichEditView :: GetParaFormatSelection](#getparaformatselection)|Récupère les attributs de mise en forme de paragraphe pour la sélection actuelle.|
|[CRichEditView :: GetPrintRect](#getprintrect)|Récupère le rectangle d’impression pour cette vue RichEdit.|
|[CRichEditView :: GetPrintWidth](#getprintwidth)|Récupère la largeur d’impression pour cette vue RichEdit.|
|[CRichEditView :: GetRichEditCtrl](#getricheditctrl)|Récupère le contrôle RichEdit.|
|[CRichEditView :: GetSelectedItem](#getselecteditem)|Récupère l’élément sélectionné à partir de la vue RichEdit.|
|[CRichEditView :: GetTextLength](#gettextlength)|Récupère la longueur du texte dans la vue RichEdit.|
|[CRichEditView :: GetTextLengthEx](#gettextlengthex)|Récupère le nombre de caractères ou d’octets dans la vue RichEdit. Liste d’indicateurs développée pour la méthode de détermination de la longueur.|
|[CRichEditView :: InsertFileAsObject](#insertfileasobject)|Insère un fichier en tant qu’élément OLE.|
|[CRichEditView :: InsertItem](#insertitem)|Insère un nouvel élément en tant qu’élément OLE.|
|[CRichEditView :: IsRichEditFormat](#isricheditformat)|Indique si le presse-papiers contient des données dans un format de modification ou de texte enrichi.|
|[CRichEditView :: OnCharEffect](#onchareffect)|Active ou désactive la mise en forme des caractères pour la sélection actuelle.|
|[CRichEditView :: OnParaAlign](#onparaalign)|Modifie l’alignement des paragraphes.|
|[CRichEditView :: OnUpdateCharEffect](#onupdatechareffect)|Met à jour l’interface utilisateur de la commande pour les fonctions membres publiques de caractères.|
|[CRichEditView :: OnUpdateParaAlign](#onupdateparaalign)|Met à jour l’interface utilisateur de la commande pour les fonctions membres publiques de paragraphe.|
|[CRichEditView ::P rintInsideRect](#printinsiderect)|Met en forme le texte spécifié dans le rectangle donné.|
|[CRichEditView ::P rintPage](#printpage)|Met en forme le texte spécifié dans la page donnée.|
|[CRichEditView :: SetCharFormat](#setcharformat)|Définit les attributs de mise en forme des caractères pour la sélection actuelle.|
|[CRichEditView :: SetMargins](#setmargins)|Définit les marges pour cette vue RichEdit.|
|[CRichEditView :: SetPaperSize](#setpapersize)|Définit le format du papier pour cette vue RichEdit.|
|[CRichEditView :: SetParaFormat](#setparaformat)|Définit les attributs de mise en forme du paragraphe pour la sélection actuelle.|
|[CRichEditView :: TextNotFound](#textnotfound)|Réinitialise l’état de recherche interne du contrôle.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CRichEditView :: GetClipboardData](#getclipboarddata)|Récupère un objet Clipboard pour une plage dans cette vue Rich Edit.|
|[CRichEditView :: GetContextMenu](#getcontextmenu)|Récupère un menu contextuel à utiliser sur le bouton droit de la souris.|
|[CRichEditView :: IsSelected](#isselected)|Indique si l’élément OLE donné est sélectionné ou non.|
|[CRichEditView :: OnFindNext](#onfindnext)|Recherche l’occurrence suivante d’une sous-chaîne.|
|[CRichEditView :: OnInitialUpdate](#oninitialupdate)|Actualise une vue lorsqu’elle est attachée pour la première fois à un document.|
|[CRichEditView :: OnPasteNativeObject](#onpastenativeobject)|Récupère les données natives d’un élément OLE.|
|[CRichEditView :: OnPrinterChanged](#onprinterchanged)|Définit les caractéristiques d’impression sur l’appareil donné.|
|[CRichEditView :: OnReplaceAll](#onreplaceall)|Remplace toutes les occurrences d’une chaîne donnée par une nouvelle chaîne.|
|[CRichEditView :: OnReplaceSel](#onreplacesel)|Remplace la sélection actuelle.|
|[CRichEditView :: OnTextNotFound](#ontextnotfound)|Gère la notification par l’utilisateur que le texte demandé est introuvable.|
|[CRichEditView :: QueryAcceptData](#queryacceptdata)|Requêtes pour voir les données sur `IDataObject` .|
|[CRichEditView :: WrapChanged](#wrapchanged)|Ajuste le périphérique de sortie cible pour cette vue RichEdit, en fonction de la valeur de `m_nWordWrap` .|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRichEditView :: m_nBulletIndent](#m_nbulletindent)|Indique la quantité de retrait pour les listes à puces.|
|[CRichEditView :: m_nWordWrap](#m_nwordwrap)|Indique les contraintes de retour automatique à la ligne.|

## <a name="remarks"></a>Notes

Un « contrôle RichEdit » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte peut être affecté à la mise en forme des caractères et des paragraphes, et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour mettre en forme le texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles pour l’utilisateur.

`CRichEditView` conserve le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` conserve la liste des éléments du client OLE qui sont dans la vue. `CRichEditCntrItem` fournit un accès côté conteneur à l’élément client OLE.

Ce contrôle commun Windows (et par conséquent l' [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes associées) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT versions 3,51 et ultérieures.

Pour obtenir un exemple d’utilisation d’une vue RichEdit dans une application MFC, consultez l’exemple d’application [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrich. h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a> CRichEditView :: AdjustDialogPosition

Appelez cette fonction pour déplacer la boîte de dialogue donnée afin qu’elle ne masque pas la sélection actuelle.

```cpp
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Paramètres

*pDlg*<br/>
Pointeur vers un `CDialog` objet.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a> CRichEditView :: CanPaste

Appelez cette fonction pour déterminer si le presse-papiers contient des informations qui peuvent être collées dans cette vue RichEdit.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le presse-papiers contient des données dans un format que cette vue RichEdit peut accepter ; Sinon, 0.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a> CRichEditView :: CRichEditView

Appelez cette fonction pour créer un `CRichEditView` objet.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a> CRichEditView ::D oPaste

Appelez cette fonction pour coller l’élément OLE dans *dataobj* dans ce document ou cette vue RichEdit.

```cpp
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Paramètres

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md) contenant les données à coller.

*Trésor*<br/>
Format du presse-papiers souhaité.

*hMetaPict*<br/>
Métafichier qui représente l’élément à coller.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction dans le cadre de l’implémentation par défaut de [QueryAcceptData](#queryacceptdata).

Cette fonction détermine le type de collage en fonction des résultats du gestionnaire pour Collage spécial. Si *CF* est égal à 0, le nouvel élément utilise la représentation sous forme actuelle. Si *CF* est différent de zéro et que *hMetaPict* n’est pas null, le nouvel élément utilise *hMetaPict* pour sa représentation.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a> CRichEditView :: FindText

Appelez cette fonction pour rechercher le texte spécifié et le définir comme étant la sélection actuelle.

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
Indique si la recherche doit correspondre à des mots entiers uniquement, et non à des parties de mots.

*bNext*<br/>
Indique la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSe, le sens de la recherche est dirigé vers le début de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le texte *lpszFind* est trouvé ; Sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction affiche le curseur d’attente pendant l’opération de recherche.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a> CRichEditView :: FindTextSimple

Appelez cette fonction pour rechercher le texte spécifié et le définir comme étant la sélection actuelle.

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
Indique si la recherche doit correspondre à des mots entiers uniquement, et non à des parties de mots.

*bNext*<br/>
Indique la direction de la recherche. Si la valeur est TRUE, le sens de la recherche est vers la fin de la mémoire tampon. Si la valeur est FALSe, le sens de la recherche est dirigé vers le début de la mémoire tampon.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si le texte *lpszFind* est trouvé ; Sinon, 0.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: FindText](#findtext).

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a> CRichEditView :: GetCharFormatSelection

Appelez cette fonction pour récupérer les attributs de mise en forme des caractères de la sélection actuelle.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Valeur renvoyée

Structure [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) qui contient les attributs de mise en forme des caractères de la sélection actuelle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez le message [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) et la structure [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a> CRichEditView :: GetClipboardData

L’infrastructure appelle cette fonction dans le cadre du traitement de [IRichEditOleCallback :: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Paramètres

*lpchrg*<br/>
Pointeur vers la structure [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) spécifiant la plage de caractères (et les éléments OLE) à copier dans l’objet de données spécifié par *lplpdataobj*.

*dwReco*<br/>
Indicateur d’opération du presse-papiers. Peut prendre l’une des valeurs suivantes.

- RECO_COPY copier dans le presse-papiers.

- RECO_CUT couper dans le presse-papiers.

- RECO_DRAG opération glisser (glisser-déplacer).

- Opération de suppression de RECO_DROP (glisser-déplacer).

- RECO_PASTE coller à partir du presse-papiers.

*lpRichDataObj*<br/>
Pointeur vers un objet [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) contenant les données du presse-papiers à partir du contrôle RichEdit ( [IRichEditOle :: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Pointeur vers la variable pointeur qui reçoit l’adresse de l' `IDataObject` objet représentant la plage spécifiée dans le paramètre *lpchrg* . La valeur de *lplpdataobj* est ignorée si une erreur est retournée.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT signalant la réussite de l’opération. Pour plus d’informations sur HRESULT, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) in the SDK Windows.

### <a name="remarks"></a>Notes

Si la valeur de retour indique une réussite, `IRichEditOleCallback::GetClipboardData` retourne le `IDataObject` accessible par *lplpdataobj*; sinon, elle retourne celle accessible par *lpRichDataObj*. Remplacez cette fonction pour fournir vos propres données du presse-papiers. L’implémentation par défaut de cette fonction retourne E_NOTIMPL.

Il s’agit d’un substituable avancé.

Pour plus d’informations, consultez [IRichEditOle :: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback :: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)et [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) dans le SDK Windows et consultez [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) dans le SDK Windows.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a> CRichEditView :: GetContextMenu

L’infrastructure appelle cette fonction dans le cadre du traitement de [IRichEditOleCallback :: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Paramètres

*seltyp*<br/>
Type de sélection. Les valeurs de type de sélection sont décrites dans la section Notes.

*lpoleobj*<br/>
Pointeur vers une `OLEOBJECT` structure qui spécifie le premier objet OLE sélectionné si la sélection contient un ou plusieurs éléments OLE. Si la sélection ne contient aucun élément, *lpoleobj* a la valeur null. La `OLEOBJECT` structure contient un pointeur vers un objet OLE v-table.

*lpchrg*<br/>
Pointeur vers une structure [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) contenant la sélection actuelle.

### <a name="return-value"></a>Valeur renvoyée

Handle vers le menu contextuel.

### <a name="remarks"></a>Notes

Cette fonction est une partie classique du traitement du bouton droit de la souris.

Le type de sélection peut être n’importe quelle combinaison des indicateurs suivants :

- SEL_EMPTY indique qu’il n’y a aucune sélection actuelle.

- SEL_TEXT indique que la sélection actuelle contient du texte.

- SEL_OBJECT indique que la sélection actuelle contient au moins un élément OLE.

- SEL_MULTICHAR indique que la sélection actuelle contient plus d’un caractère de texte.

- SEL_MULTIOBJECT indique que la sélection actuelle contient plus d’un objet OLE.

L’implémentation par défaut retourne la valeur NULL. Il s’agit d’un substituable avancé.

Pour plus d’informations, consultez [IRichEditOleCallback :: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) et [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) dans le SDK Windows.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a> CRichEditView :: GetDocument

Appelez cette fonction pour obtenir un pointeur vers le `CRichEditDoc` associé à cette vue.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) associé à votre `CRichEditView` objet.

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a> CRichEditView :: GetInPlaceActiveItem

Appelez cette fonction pour récupérer l’élément OLE actuellement activé sur place dans cet `CRichEditView` objet.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) actif unique dans cette vue Rich Edit ; NULL s’il n’existe aucun élément OLE actuellement dans l’état actif sur place.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a> CRichEditView :: GetMargins

Appelez cette fonction pour récupérer les marges actuelles utilisées dans l’impression.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Valeur renvoyée

Marges utilisées pour l’impression, mesurées en MM_TWIPS.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a> CRichEditView :: GetPageRect

Appelez cette fonction pour récupérer les dimensions de la page utilisée dans l’impression.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Valeur renvoyée

Les limites de la page utilisée pour l’impression, mesurées en MM_TWIPS.

### <a name="remarks"></a>Notes

Cette valeur est basée sur le format du papier.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a> CRichEditView :: GetPaperSize

Appelez cette fonction pour récupérer le format de papier actuel.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valeur renvoyée

Taille du papier utilisé pour l’impression, mesurée en MM_TWIPS.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a> CRichEditView :: GetParaFormatSelection

Appelez cette fonction pour récupérer les attributs de mise en forme de paragraphe de la sélection actuelle.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Valeur renvoyée

Structure [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) qui contient les attributs de mise en forme de paragraphe de la sélection actuelle.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) la structure message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) dans le SDK Windows.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a> CRichEditView :: GetPrintRect

Appelez cette fonction pour récupérer les limites de la zone d’impression dans le rectangle de page.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Valeur renvoyée

Les limites de la zone d’image utilisée pour l’impression, mesurées en MM_TWIPS.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a> CRichEditView :: GetPrintWidth

Appelez cette fonction pour déterminer la largeur de la zone d’impression.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Valeur renvoyée

Largeur de la zone d’impression, mesurée en MM_TWIPS.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a> CRichEditView :: GetRichEditCtrl

Appelez cette fonction pour récupérer l’objet [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) associé à l' `CRichEditView` objet.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Valeur renvoyée

`CRichEditCtrl`Objet pour cette vue.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: FindText](#findtext).

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a> CRichEditView :: GetSelectedItem

Appelez cette fonction pour récupérer l’élément OLE (un `CRichEditCntrItem` objet) actuellement sélectionné dans cet `CRichEditView` objet.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) sélectionné dans l' `CRichEditView` objet ; NULL si aucun élément n’est sélectionné dans cette vue.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a> CRichEditView :: GetTextLength

Appelez cette fonction pour récupérer la longueur du texte dans cet `CRichEditView` objet.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Valeur renvoyée

Longueur du texte dans cet `CRichEditView` objet.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a> CRichEditView :: GetTextLengthEx

Appelez cette fonction membre pour calculer la longueur du texte dans cet `CRichEditView` objet.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Paramètres

*dwFlags*<br/>
Valeur spécifiant la méthode à utiliser pour déterminer la longueur du texte. Ce membre peut être une ou plusieurs des valeurs répertoriées dans le membre Flags de [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) décrit dans la SDK Windows.

*uCodePage*<br/>
Page de codes pour la traduction (CP_ACP pour la page de codes ANSI, 1200 pour Unicode).

### <a name="return-value"></a>Valeur renvoyée

Nombre de caractères ou d’octets dans le contrôle d’édition. Si des indicateurs incompatibles ont été définis dans *dwFlags*, cette fonction membre retourne E_INVALIDARG.

### <a name="remarks"></a>Notes

`GetTextLengthEx` fournit des méthodes supplémentaires pour déterminer la longueur du texte. Il prend en charge la fonctionnalité Rich Edit 2,0. Pour plus d’informations, consultez [à propos des contrôles RichEdit](/windows/win32/Controls/about-rich-edit-controls) dans le SDK Windows.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a> CRichEditView :: InsertFileAsObject

Appelez cette fonction pour insérer le fichier spécifié (sous la forme d’un objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) ) dans un affichage RichEdit.

```cpp
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Paramètres

*lpszFileName*<br/>
Chaîne contenant le nom du fichier à insérer.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a> CRichEditView :: InsertItem

Appelez cette fonction pour insérer un objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) dans un affichage RichEdit.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Paramètres

*pItem*<br/>
Pointeur vers l’élément à insérer.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT indiquant la réussite de l’insertion.

### <a name="remarks"></a>Notes

Pour plus d’informations sur HRESULT, consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) in the SDK Windows.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a> CRichEditView :: IsRichEditFormat

Appelez cette fonction pour déterminer si *CF* est un format de presse-papiers qui est du texte, du texte enrichi ou du texte enrichi avec des éléments OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Paramètres

*Trésor*<br/>
Format du presse-papiers qui vous intéresse.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si *CF* est un format de presse-papiers de modification ou de texte enrichi.

## <a name="cricheditviewisselected"></a><a name="isselected"></a> CRichEditView :: IsSelected

Appelez cette fonction pour déterminer si l’élément OLE spécifié est actuellement sélectionné dans cette vue.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Paramètres

*pDocItem*<br/>
Pointeur vers un objet dans la vue.

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’objet est sélectionné ; Sinon, 0.

### <a name="remarks"></a>Notes

Substituez cette fonction si votre classe d’affichage dérivée a une méthode différente pour gérer la sélection des éléments OLE.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a> CRichEditView :: m_nBulletIndent

Mise en retrait pour les éléments de puce dans une liste ; par défaut, 720 unités, soit 1/2 pouce.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a> CRichEditView :: m_nWordWrap

Indique le type de retour automatique à la ligne pour cette vue RichEdit.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Notes

Une des valeurs suivantes :

- `WrapNone` Indique l’absence de retour automatique à la disposition automatique.

- `WrapToWindow` Indique le retour automatique à la fenêtre en fonction de la largeur de la fenêtre.

- `WrapToTargetDevice` Indique le retour automatique à la disposition des mots selon les caractéristiques de l’appareil cible.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: WrapChanged](#wrapchanged).

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a> CRichEditView :: OnCharEffect

Appelez cette fonction pour basculer les effets de mise en forme des caractères pour la sélection actuelle.

```cpp
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Paramètres

*dwMask*<br/>
Effets de la mise en forme des caractères à modifier dans la sélection actuelle.

*dwEffect*<br/>
Liste souhaitée des effets de la mise en forme des caractères à activer/désactiver.

### <a name="remarks"></a>Notes

Chaque appel à cette fonction bascule les effets de mise en forme spécifiés pour la sélection actuelle.

Pour plus d’informations sur les paramètres *dwMask* et *dwEffect* et leurs valeurs potentielles, consultez les membres de données correspondants de [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a> CRichEditView :: OnFindNext

Appelé par le Framework lors du traitement des commandes à partir de la boîte de dialogue Rechercher/Remplacer.

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

*bNext*<br/>
La direction de la recherche : TRUE indique le bas ; FALSe, vers le haut.

*bCase*<br/>
Indique si la recherche doit respecter la casse.

*bWord*<br/>
Indique si la recherche doit faire correspondre uniquement les mots entiers.

### <a name="remarks"></a>Notes

Appelez cette fonction pour rechercher du texte dans le `CRichEditView` . Remplacez cette fonction pour modifier les caractéristiques de recherche de votre classe de vue dérivée.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a> CRichEditView :: OnInitialUpdate

Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle la fonction membre [CView :: OnUpdate](../../mfc/reference/cview-class.md#onupdate) sans informations d’indication (autrement dit, en utilisant les valeurs par défaut 0 pour le paramètre *lHint* et null pour le paramètre *pHint* ). Substituez cette fonction pour exécuter une initialisation unique qui nécessite des informations sur le document. Par exemple, si votre application comporte des documents de taille fixe, vous pouvez utiliser cette fonction pour initialiser les limites de défilement d’une vue en fonction de la taille du document. Si votre application prend en charge les documents de taille variable, utilisez `OnUpdate` pour mettre à jour les limites de défilement chaque fois que le document change.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: m_nWordWrap](#m_nwordwrap).

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a> CRichEditView :: OnPasteNativeObject

Utilisez cette fonction pour charger des données natives à partir d’un élément incorporé.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Paramètres

*lpStg*<br/>
Pointeur vers un objet [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) .

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; Sinon, 0 ;

### <a name="remarks"></a>Notes

En règle générale, vous devez créer un [COleStreamFile](../../mfc/reference/colestreamfile-class.md) autour de `IStorage` . `COleStreamFile`Peut être attaché à une archive et à [CObject :: Serialize](../../mfc/reference/cobject-class.md#serialize) appelée pour charger les données.

Il s’agit d’un substituable avancé.

Pour plus d’informations, consultez [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) dans le SDK Windows.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a> CRichEditView :: OnParaAlign

Appelez cette fonction pour modifier l’alignement du paragraphe pour les paragraphes sélectionnés.

```cpp
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Paramètres

*wAlign*<br/>
Alignement de paragraphe souhaité. Une des valeurs suivantes :

- PFA_LEFT aligner les paragraphes avec la marge de gauche.

- PFA_RIGHT aligner les paragraphes avec la marge de droite.

- PFA_CENTER centrer les paragraphes entre les marges.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a> CRichEditView :: OnPrinterChanged

Remplacez cette fonction pour modifier les caractéristiques de cette vue RichEdit lorsque l’imprimante change.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Paramètres

*dcPrinter*<br/>
Objet [CDC](../../mfc/reference/cdc-class.md) pour la nouvelle imprimante.

### <a name="remarks"></a>Notes

L’implémentation par défaut définit le format du papier sur la hauteur et la largeur physiques du périphérique de sortie (imprimante). Si aucun contexte de périphérique n’est associé à *dcPrinter*, l’implémentation par défaut définit le format de papier sur 8,5 par 11 pouces.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a> CRichEditView :: OnReplaceAll

Appelé par le Framework lors du traitement des commandes remplacer toutes de la boîte de dialogue remplacer.

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
Texte de remplacement.

*bCase*<br/>
Indique si la recherche respecte la casse.

*bWord*<br/>
Indique si la recherche doit sélectionner des mots entiers ou non.

### <a name="remarks"></a>Notes

Appelez cette fonction pour remplacer toutes les occurrences d’un texte donné par une autre chaîne. Remplacez cette fonction pour modifier les caractéristiques de recherche pour cette vue.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: FindText](#findtext).

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a> CRichEditView :: OnReplaceSel

Appelé par le Framework lors du traitement des commandes de remplacement à partir de la boîte de dialogue remplacer.

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

*bNext*<br/>
Indique la direction de la recherche : TRUE est en bas ; FALSe, vers le haut.

*bCase*<br/>
Indique si la recherche respecte la casse.

*bWord*<br/>
Indique si la recherche doit sélectionner des mots entiers ou non.

*lpszReplace*<br/>
Texte de remplacement.

### <a name="remarks"></a>Notes

Appelez cette fonction pour remplacer une occurrence d’un texte donné par une autre chaîne. Remplacez cette fonction pour modifier les caractéristiques de recherche pour cette vue.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a> CRichEditView :: OnTextNotFound

Appelée par l’infrastructure chaque fois qu’une recherche échoue.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Texte introuvable.

### <a name="remarks"></a>Notes

Substituez cette fonction pour modifier la notification de sortie à partir d’un [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Pour plus d’informations, consultez [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a> CRichEditView :: OnUpdateCharEffect

L’infrastructure appelle cette fonction pour mettre à jour l’interface utilisateur de commande pour les commandes d’effet de caractère.

```cpp
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) .

*dwMask*<br/>
Indique le masque de mise en forme des caractères.

*dwEffect*<br/>
Indique l’effet de mise en forme des caractères.

### <a name="remarks"></a>Notes

Le masque *dwMask* spécifie les attributs de mise en forme de caractères à vérifier. Les indicateurs *dwEffect* répertorient les attributs de mise en forme de caractères à définir/effacer.

Pour plus d’informations sur les paramètres *dwMask* et *dwEffect* et leurs valeurs potentielles, consultez les membres de données correspondants de [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a> CRichEditView :: OnUpdateParaAlign

L’infrastructure appelle cette fonction pour mettre à jour l’interface utilisateur de commande pour les commandes d’effet de paragraphe.

```cpp
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Paramètres

*pCmdUI*<br/>
Pointeur vers un objet [CCmdUI](../../mfc/reference/ccmdui-class.md) .

*wAlign*<br/>
Alignement du paragraphe à vérifier. Une des valeurs suivantes :

- PFA_LEFT aligner les paragraphes avec la marge de gauche.

- PFA_RIGHT aligner les paragraphes avec la marge de droite.

- PFA_CENTER centrer les paragraphes entre les marges.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a> CRichEditView ::P rintInsideRect

Appelez cette fonction pour mettre en forme une plage de texte dans un contrôle Rich Edit afin qu’elle tienne dans *rectLayout* pour l’appareil spécifié par le *contrôleur de domaine principal*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers un contexte de périphérique pour la zone de sortie.

*rectLayout*<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect) ou [CRect](../../atl-mfc-shared/reference/crect-class.md) qui définit la zone de sortie.

*nIndexStart*<br/>
Index de base zéro du premier caractère à mettre en forme.

*nIndexStop*<br/>
Index de base zéro du dernier caractère à mettre en forme.

*bOutput*<br/>
Indique si le texte doit être rendu. Si la valeur est FALSe, le texte est uniquement mesuré.

### <a name="return-value"></a>Valeur renvoyée

Index du dernier caractère qui tient dans la zone de sortie plus un.

### <a name="remarks"></a>Notes

En général, cet appel est suivi par un appel à [CRichEditCtrl ::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) qui génère la sortie.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: GetPaperSize](#getpapersize).

## <a name="cricheditviewprintpage"></a><a name="printpage"></a> CRichEditView ::P rintPage

Appelez cette fonction pour mettre en forme une plage de texte dans un contrôle Rich Edit pour le périphérique de sortie spécifié par le *contrôleur de domaine principal*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
Pointeur vers un contexte de périphérique pour la sortie de page.

*nIndexStart*<br/>
Index de base zéro du premier caractère à mettre en forme.

*nIndexStop*<br/>
Index de base zéro du dernier caractère à mettre en forme.

### <a name="return-value"></a>Valeur renvoyée

Index du dernier caractère qui tient sur la page plus un.

### <a name="remarks"></a>Notes

La disposition de chaque page est contrôlée par [GetPageRect](#getpagerect) et [GetPrintRect](#getprintrect). En général, cet appel est suivi par un appel à [CRichEditCtrl ::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) qui génère la sortie.

Notez que les marges sont relatives à la page physique, et non à la page logique. Ainsi, les marges de zéro découpent souvent le texte, car de nombreuses imprimantes comportent des zones non imprimables sur la page. Pour éviter de découper votre texte, vous devez appeler [setMargins](#setmargins) et définir des marges raisonnables avant l’impression.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a> CRichEditView :: QueryAcceptData

Appelé par l’infrastructure pour coller un objet dans la modification enrichie.

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
Pointeur vers l' [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) à interroger.

*lpcfFormat*<br/>
Pointeur vers le format de données acceptable.

*dwReco*<br/>
Non utilisé.

*bReally*<br/>
Indique si l’opération de collage doit continuer ou non.

*hMetaFile*<br/>
Handle du métafichier utilisé pour dessiner l’icône de l’élément.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT signalant la réussite de l’opération.

### <a name="remarks"></a>Notes

Substituez cette fonction pour gérer différentes organisations d’éléments COM dans votre classe de document dérivée. Il s’agit d’un substituable avancé.

Pour plus d’informations sur HRESULT et `IDataObject` , consultez [structure of com Error Codes](/windows/win32/com/structure-of-com-error-codes) and [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), respectivement, dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a> CRichEditView :: SetCharFormat

Appelez cette fonction pour définir les attributs de mise en forme des caractères pour le nouveau texte dans cet `CRichEditView` objet.

```cpp
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Paramètres

*Trésor*<br/>
Structure [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) contenant les nouveaux attributs de mise en forme de caractères par défaut.

### <a name="remarks"></a>Notes

Seuls les attributs spécifiés par le `dwMask` membre de *CF* sont modifiés par cette fonction.

Pour plus d’informations, consultez [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) la structure message and [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a> CRichEditView :: SetMargins

Appelez cette fonction pour définir les marges d’impression de cette vue RichEdit.

```cpp
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Paramètres

*rectMargin*<br/>
Nouvelles valeurs de marge pour l’impression, mesurées en MM_TWIPS.

### <a name="remarks"></a>Notes

Si [m_nWordWrap](#m_nwordwrap) est `WrapToTargetDevice` , vous devez appeler [WrapChanged](#wrapchanged) après avoir utilisé cette fonction pour ajuster les caractéristiques d’impression.

Notez que les marges utilisées par [PrintPage](#printpage) sont relatives à la page physique, et non à la page logique. Ainsi, les marges de zéro découpent souvent le texte, car de nombreuses imprimantes comportent des zones non imprimables sur la page. Pour éviter de découper votre texte, vous devez appeler utiliser `SetMargins` pour définir des marges d’impression raisonnables avant l’impression.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: GetPaperSize](#getpapersize).

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a> CRichEditView :: SetPaperSize

Appelez cette fonction pour définir le format de papier pour l’impression de cette vue RichEdit.

```cpp
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Paramètres

*sizePaper*<br/>
Nouvelles valeurs de format de papier pour l’impression, mesurées en MM_TWIPS.

### <a name="remarks"></a>Notes

Si [m_nWordWrap](#m_nwordwrap) est `WrapToTargetDevice` , vous devez appeler [WrapChanged](#wrapchanged) après avoir utilisé cette fonction pour ajuster les caractéristiques d’impression.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a> CRichEditView :: SetParaFormat

Appelez cette fonction pour définir les attributs de mise en forme de paragraphe pour la sélection actuelle dans cet `CRichEditView` objet.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Paramètres

*util*<br/>
Structure [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) contenant les nouveaux attributs de mise en forme des paragraphes par défaut.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; Sinon, 0.

### <a name="remarks"></a>Notes

Seuls les attributs spécifiés par le `dwMask` membre de *PF* sont modifiés par cette fonction.

Pour plus d’informations, consultez [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) la structure message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) dans le SDK Windows.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a> CRichEditView :: TextNotFound

Appelez cette fonction pour réinitialiser l’état de recherche interne du contrôle [CRichEditView](../../mfc/reference/cricheditview-class.md) après l’échec d’un appel à [TexteCherché](#findtext).

```cpp
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Paramètres

*lpszFind*<br/>
Contient la chaîne de texte qui est introuvable.

### <a name="remarks"></a>Notes

Il est recommandé d’appeler cette méthode immédiatement après l’échec des appels à [TexteCherché](#findtext) , afin que l’état de recherche interne du contrôle soit correctement réinitialisé.

Le paramètre *lpszFind* doit inclure le même contenu que la chaîne fournie à [TexteCherché](#findtext). Après la réinitialisation de l’état de recherche interne, cette méthode appellera la méthode [OnTextNotFound](#ontextnotfound) avec la chaîne de recherche fournie.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CRichEditView :: FindText](#findtext).

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a> CRichEditView :: WrapChanged

Appelez cette fonction lorsque les caractéristiques d’impression ont changé ( [setMargins](#setmargins) ou [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Notes

Remplacez cette fonction pour modifier la façon dont la vue RichEdit réagit aux modifications apportées à [m_nWordWrap](#m_nwordwrap) ou aux caractéristiques d’impression ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView, classe](../../mfc/reference/cctrlview-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc, classe](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem, classe](../../mfc/reference/cricheditcntritem-class.md)
