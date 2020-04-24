---
title: CPrintInfo, structure
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 3b081b0728514c0fca2eb31462e1bcd9e91a47aa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753011"
---
# <a name="cprintinfo-structure"></a>CPrintInfo, structure

Stocke des informations sur un travail d’impression ou d’impression.

## <a name="syntax"></a>Syntaxe

```
struct CPrintInfo
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPrintInfo::GetDePage](#getfrompage)|Retourne le numéro de la première page imprimée.|
|[CPrintInfo::GetMaxPage](#getmaxpage)|Retourne le numéro de la dernière page du document.|
|[CPrintInfo::GetMinPage](#getminpage)|Retourne le numéro de la première page du document.|
|[CPrintInfo::GetOffsetPage](#getoffsetpage)|Retourne le nombre de pages précédant la première page d’un article DocObject imprimé dans un travail d’impression DocObject combiné.|
|[CPrintInfo::GetToPage](#gettopage)|Retourne le numéro de la dernière page imprimée.|
|[CPrintInfo::SetMaxPage](#setmaxpage)|Définit le numéro de la dernière page du document.|
|[CPrintInfo::SetMinPage](#setminpage)|Définit le numéro de la première page du document.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintInfo:m_bContinuePrinting](#m_bcontinueprinting)|Contient un drapeau indiquant si le cadre doit continuer la boucle d’impression.|
|[CPrintInfo:m_bDirect](#m_bdirect)|Contient un drapeau indiquant si le document est imprimé directement (sans afficher la boîte de dialogue d’impression).|
|[CPrintInfo:m_bDocObject](#m_bdocobject)|Contient un drapeau indiquant si le document imprimé est un DocObject.|
|[CPrintInfo:m_bPreview](#m_bpreview)|Contient un drapeau indiquant si le document est prévisualisé.|
|[CPrintInfo:m_dwFlags](#m_dwflags)|Spécifie les opérations d’impression DocObject.|
|[CPrintInfo:m_lpUserData](#m_lpuserdata)|Contient un pointeur sur une structure créée par l’utilisateur.|
|[CPrintInfo:m_nCurPage](#m_ncurpage)|Identifie le numéro de la page actuellement imprimée.|
|[CPrintInfo:m_nJobNumber](#m_njobnumber)|Spécifie le numéro d’emploi attribué par le système d’exploitation pour le travail d’impression actuel|
|[CPrintInfo:m_nNumPreviewPages](#m_nnumpreviewpages)|Identifie le nombre de pages affichées dans la fenêtre d’aperçu; soit 1 ou 2.|
|[CPrintInfo:m_nOffsetPage](#m_noffsetpage)|Spécifie le décalage de la première page d’un DocObject particulier dans un travail d’impression DocObject combiné.|
|[CPrintInfo:m_pPD](#m_ppd)|Contient un pointeur sur l’objet `CPrintDialog` utilisé pour la boîte de dialogue d’impression.|
|[CPrintInfo:m_rectDraw](#m_rectdraw)|Spécifie un rectangle définissant la zone de page utilisable actuelle.|
|[CPrintInfo:m_strPageDesc](#m_strpagedesc)|Contient une chaîne de format pour l’affichage du numéro de page.|

## <a name="remarks"></a>Notes

`CPrintInfo`est une structure et n’a pas de classe de base.

Le cadre crée `CPrintInfo` un objet de chaque fois que la commande d’impression ou d’aperçu d’impression est choisie et la détruit lorsque la commande est terminée.

`CPrintInfo`contient des informations sur l’ensemble du travail d’impression, comme la gamme de pages à imprimer, et l’état actuel du travail d’impression, comme la page en cours d’impression. Certaines informations sont stockées dans un objet [CPrintDialog](../../mfc/reference/cprintdialog-class.md) associé; cet objet contient les valeurs saisies par l’utilisateur dans la boîte de dialogue d’impression.

Un `CPrintInfo` objet est passé entre le cadre et votre classe de vue pendant le processus d’impression et est utilisé pour échanger des informations entre les deux. Par exemple, le cadre informe la classe de vue quelle page `m_nCurPage` du `CPrintInfo`document imprimer en attribuant une valeur au membre de ; la classe de vue récupère la valeur et effectue l’impression réelle de la page spécifiée.

Un autre exemple est le cas dans lequel la longueur du document n’est pas connue jusqu’à ce qu’il soit imprimé. Dans cette situation, la classe de vue teste pour la fin du document chaque fois qu’une page est imprimée. Lorsque la fin est atteinte, `m_bContinuePrinting` la `CPrintInfo` classe de vue définit le membre de FALSE; cela informe le cadre pour arrêter la boucle d’impression.

`CPrintInfo`est utilisé par les `CView` fonctions membres de énumérés sous "Voir aussi." Pour plus d’informations sur l’architecture d’impression fournie par la Microsoft Foundation Class Library, voir [Frame Windows](../../mfc/frame-windows.md) et [Document/View Architecture](../../mfc/document-view-architecture.md) et les articles [Printing](../../mfc/printing.md) and [Printing: Multipage Documents](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPrintInfo`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a>CPrintInfo::GetDePage

Appelez cette fonction pour récupérer le numéro de la première page à imprimer.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de la première page à imprimer.

### <a name="remarks"></a>Notes

Il s’agit de la valeur spécifiée par l’utilisateur `CPrintDialog` dans la boîte `m_pPD` de dialogue d’impression, et elle est stockée dans l’objet référencé par le membre. Si l’utilisateur n’a pas précisé de valeur, la valeur par défaut est la première page du document.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a>CPrintInfo::GetMaxPage

Appelez cette fonction pour récupérer le numéro de la dernière page du document.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de la dernière page du document.

### <a name="remarks"></a>Notes

Cette valeur est `CPrintDialog` stockée dans l’objet référencé par le `m_pPD` membre.

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a>CPrintInfo::GetMinPage

Appelez cette fonction pour récupérer le numéro de la première page du document.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de la première page du document.

### <a name="remarks"></a>Notes

Cette valeur est `CPrintDialog` stockée dans l’objet référencé par le `m_pPD` membre.

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a>CPrintInfo::GetOffsetPage

Appelez cette fonction pour récupérer le décalage lors de l’impression de plusieurs articles DocObject d’un client DocObject.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de pages précédant la première page d’un article DocObject imprimé dans un travail d’impression DocObject combiné.

### <a name="remarks"></a>Notes

Cette valeur est référencée par le `m_nOffsetPage` membre. La première page de votre document `m_nOffsetPage` sera numérotée de la valeur 1 lorsqu’elle sera imprimée sous forme de DocObject avec d’autres documents actifs. Le `m_nOffsetPage` membre n’est `m_bDocObject` valide que si la valeur est VRAIE.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a>CPrintInfo::GetToPage

Appelez cette fonction pour récupérer le numéro de la dernière page à imprimer.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Valeur de retour

Le numéro de la dernière page à imprimer.

### <a name="remarks"></a>Notes

Il s’agit de la valeur spécifiée par l’utilisateur `CPrintDialog` dans la boîte `m_pPD` de dialogue d’impression, et elle est stockée dans l’objet référencé par le membre. Si l’utilisateur n’a pas précisé de valeur, la valeur par défaut est la dernière page du document.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a>CPrintInfo:m_bContinuePrinting

Contient un drapeau indiquant si le cadre doit continuer la boucle d’impression.

### <a name="remarks"></a>Notes

Si vous effectuez une pagination à temps d’impression, vous `CView::OnPrepareDC` pouvez définir ce membre à FALSE dans votre remplacement d’une fois la fin du document atteint. Vous n’avez pas à modifier cette variable si vous avez spécifié la `SetMaxPage` longueur du document au début du travail d’impression en utilisant la fonction membre. Le `m_bContinuePrinting` membre est une variable publique de type BOOL.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a>CPrintInfo:m_bDirect

Le cadre définit ce membre à VRAI si la boîte de dialogue d’impression sera contournée pour l’impression directe ; FALSE autrement.

### <a name="remarks"></a>Notes

Le dialogue d’impression est normalement contourné lorsque vous imprimez à partir de la coque ou lorsque l’impression est effectuée à l’aide de l’ID de commande ID_FILE_PRINT_DIRECT.

Normalement, vous ne changez pas ce membre, mais si vous le changez, changez-le avant d’appeler [CView::DoPreparePrinting](../../mfc/reference/cview-class.md#doprepareprinting) dans votre remplacement de [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a>CPrintInfo:m_bDocObject

Contient un drapeau indiquant si le document imprimé est un DocObject.

### <a name="remarks"></a>Notes

Les `m_dwFlags` membres `m_nOffsetPage` des données et sont invalides à moins que ce drapeau soit VRAI.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a>CPrintInfo:m_bPreview

Contient un drapeau indiquant si le document est prévisualisé.

### <a name="remarks"></a>Notes

Ceci est défini par le cadre en fonction de la commande de l’utilisateur exécuté. La boîte de dialogue Print n’est pas affichée pour un travail d’impression-aperçu. Le `m_bPreview` membre est une variable publique de type BOOL.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a>CPrintInfo:m_dwFlags

Contient une combinaison de drapeaux spécifiant les opérations d’impression DocObject.

### <a name="remarks"></a>Notes

Valable uniquement si `m_bDocObject` le membre des données est VRAI.

Les drapeaux peuvent être une ou plusieurs des valeurs suivantes :

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a>CPrintInfo:m_lpUserData

Contient un pointeur sur une structure créée par l’utilisateur.

### <a name="remarks"></a>Notes

Vous pouvez l’utiliser pour stocker des données spécifiques à l’impression que vous ne souhaitez pas stocker dans votre classe de vue. Le `m_lpUserData` membre est une variable publique de type LPVOID.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a>CPrintInfo:m_nCurPage

Contient le numéro de la page actuelle.

### <a name="remarks"></a>Notes

Le cadre `CView::OnPrepareDC` `CView::OnPrint` appelle et une fois pour chaque page du document, en précisant une valeur différente pour ce membre à chaque fois; ses valeurs vont de `GetFromPage` la valeur `GetToPage`retournée par à celui retourné par . Utilisez ce membre dans vos `CView::OnPrepareDC` `CView::OnPrint` remplacements et pour imprimer la page spécifiée du document.

Lorsque le mode de prévisualisation est invoqué pour la première fois, le cadre lit la valeur de ce membre pour déterminer quelle page du document doit être aperçue au départ. Vous pouvez définir la valeur de ce `CView::OnPreparePrinting` membre dans votre remplacement pour maintenir la position actuelle de l’utilisateur dans le document lors de la saisie du mode aperçu. Le `m_nCurPage` membre est une variable publique de type UINT.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a>CPrintInfo:m_nJobNumber

Indique le numéro d’emploi attribué par le système d’exploitation pour le travail d’impression actuel.

### <a name="remarks"></a>Notes

Cette valeur peut être SP_ERROR si le travail n’a pas `CPrintInfo` encore imprimé (c’est-à-dire si l’objet est nouvellement construit et n’a pas encore été utilisé pour imprimer), ou s’il y avait une erreur dans le démarrage du travail.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a>CPrintInfo:m_nNumPreviewPages

Contient le nombre de pages affichées en mode aperçu; il peut être soit 1 ou 2.

### <a name="remarks"></a>Notes

Le `m_nNumPreviewPages` membre est une variable publique de type UINT.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a>CPrintInfo:m_nOffsetPage

Contient le nombre de pages précédant la première page d’un DocObject particulier dans un travail d’impression DocObject combiné.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a>CPrintInfo:m_pPD

Contient un pointeur sur l’objet `CPrintDialog` utilisé pour afficher la boîte de dialogue d’impression pour le travail d’impression.

### <a name="remarks"></a>Notes

Le `m_pPD` membre est une variable publique `CPrintDialog`déclarée comme un pointeur à .

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a>CPrintInfo:m_rectDraw

Spécifie la zone de dessin utilisable de la page dans les coordonnées logiques.

### <a name="remarks"></a>Notes

Vous voudrez peut-être vous référer `CView::OnPrint`à cela dans votre remplacement de . Vous pouvez utiliser ce membre pour garder une trace de ce que la zone reste utilisable après que vous imprimez des en-têtes, des pieds, et ainsi de suite. Le `m_rectDraw` membre est une `CRect`variable publique de type .

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a>CPrintInfo:m_strPageDesc

Contient une chaîne de format utilisée pour afficher les numéros de page pendant l’aperçu d’impression ; cette chaîne se compose de deux sous-cordes, l’une pour l’affichage d’une seule page et l’autre pour l’affichage de double page, chacune terminée par un caractère 'n'.

### <a name="remarks"></a>Notes

Le cadre utilise la valeur par défaut de « Page % u’nPages % u-%u’n ». Si vous voulez un format différent pour les numéros de `CView::OnPreparePrinting`page, spécifiez une chaîne de format dans votre remplacement de . Le `m_strPageDesc` membre est une `CString`variable publique de type .

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a>CPrintInfo::SetMaxPage

Appelez cette fonction pour spécifier le numéro de la dernière page du document.

```cpp
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Paramètres

*nMaxPage (en)*<br/>
Numéro de la dernière page du document.

### <a name="remarks"></a>Notes

Cette valeur est `CPrintDialog` stockée dans l’objet référencé par le `m_pPD` membre. Si la longueur du document est connue avant qu’il ne `CView::OnPreparePrinting`soit imprimé, appelez cette fonction à partir de votre remplacement de . Si la longueur du document dépend d’un paramètre spécifié par l’utilisateur dans `CView::OnBeginPrinting`la boîte de dialogue d’impression, appelez cette fonction à partir de votre remplacement de . Si la longueur du document n’est pas `m_bContinuePrinting` connue tant qu’il n’est pas imprimé, utilisez-le pour contrôler la boucle d’impression.

### <a name="example"></a>Exemple

  Voir l’exemple pour [CView:OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a>CPrintInfo::SetMinPage

Appelez cette fonction pour spécifier le numéro de la première page du document.

```cpp
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Paramètres

*nMinPage*<br/>
Numéro de la première page du document.

### <a name="remarks"></a>Notes

Les numéros de page commencent normalement à 1. Cette valeur est `CPrintDialog` stockée dans l’objet référencé par le `m_pPD` membre.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView::OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView::OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView::OnPrint](../../mfc/reference/cview-class.md#onprint)
