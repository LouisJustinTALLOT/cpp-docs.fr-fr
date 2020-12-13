---
description: 'En savoir plus sur : CPrintInfo, structure'
title: CPrintInfo (structure)
ms.date: 11/04/2016
f1_keywords:
- CPrintInfo
helpviewer_keywords:
- CPrintInfo structure [MFC]
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
ms.openlocfilehash: 355bcf2f04b32756ae16147465054e945d70cf78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343386"
---
# <a name="cprintinfo-structure"></a>CPrintInfo (structure)

Stocke des informations sur un travail d’impression ou d’aperçu avant impression.

## <a name="syntax"></a>Syntaxe

```
struct CPrintInfo
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPrintInfo :: GetFromPage](#getfrompage)|Retourne le numéro de la première page en cours d’impression.|
|[CPrintInfo :: GetMaxPage](#getmaxpage)|Retourne le numéro de la dernière page du document.|
|[CPrintInfo :: GetMinPage](#getminpage)|Retourne le numéro de la première page du document.|
|[CPrintInfo :: GetOffsetPage](#getoffsetpage)|Retourne le nombre de pages précédant la première page d’un élément DocObject en cours d’impression dans un travail d’impression de DocObject combiné.|
|[CPrintInfo :: GetToPage](#gettopage)|Retourne le numéro de la dernière page en cours d’impression.|
|[CPrintInfo :: SetMaxPage](#setmaxpage)|Définit le numéro de la dernière page du document.|
|[CPrintInfo :: SetMinPage](#setminpage)|Définit le numéro de la première page du document.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPrintInfo :: m_bContinuePrinting](#m_bcontinueprinting)|Contient un indicateur qui spécifie si l’infrastructure doit continuer la boucle d’impression.|
|[CPrintInfo :: m_bDirect](#m_bdirect)|Contient un indicateur qui spécifie si le document est imprimé directement (sans afficher la boîte de dialogue Imprimer).|
|[CPrintInfo :: m_bDocObject](#m_bdocobject)|Contient un indicateur qui spécifie si le document en cours d’impression est un DocObject.|
|[CPrintInfo :: m_bPreview](#m_bpreview)|Contient un indicateur qui spécifie si l’aperçu du document est en cours.|
|[CPrintInfo :: m_dwFlags](#m_dwflags)|Spécifie les opérations d’impression DocObject.|
|[CPrintInfo :: m_lpUserData](#m_lpuserdata)|Contient un pointeur vers une structure créée par l’utilisateur.|
|[CPrintInfo :: m_nCurPage](#m_ncurpage)|Identifie le numéro de la page en cours d’impression.|
|[CPrintInfo :: m_nJobNumber](#m_njobnumber)|Spécifie le numéro de travail attribué par le système d’exploitation pour le travail d’impression en cours|
|[CPrintInfo :: m_nNumPreviewPages](#m_nnumpreviewpages)|Identifie le nombre de pages affichées dans la fenêtre d’aperçu ; 1 ou 2.|
|[CPrintInfo :: m_nOffsetPage](#m_noffsetpage)|Spécifie le décalage de la première page d’un DocObject particulier dans un travail d’impression en mode DocObject combiné.|
|[CPrintInfo :: m_pPD](#m_ppd)|Contient un pointeur vers l' `CPrintDialog` objet utilisé pour la boîte de dialogue Imprimer.|
|[CPrintInfo :: m_rectDraw](#m_rectdraw)|Spécifie un rectangle définissant la zone de page utilisable actuelle.|
|[CPrintInfo :: m_strPageDesc](#m_strpagedesc)|Contient une chaîne de format pour l’affichage du numéro de page.|

## <a name="remarks"></a>Notes

`CPrintInfo` est une structure et n’a pas de classe de base.

L’infrastructure crée un objet `CPrintInfo` chaque fois que la commande Imprimer ou aperçu avant impression est sélectionnée et détruite à la fin de la commande.

`CPrintInfo` contient des informations sur le travail d’impression dans son ensemble, telles que la plage de pages à imprimer et l’état actuel du travail d’impression, tel que la page actuellement imprimée. Certaines informations sont stockées dans un objet [CPrintDialog](../../mfc/reference/cprintdialog-class.md) associé ; cet objet contient les valeurs entrées par l’utilisateur dans la boîte de dialogue Imprimer.

Un `CPrintInfo` objet est passé entre l’infrastructure et votre classe d’affichage pendant le processus d’impression et est utilisé pour échanger des informations entre les deux. Par exemple, le Framework informe la classe d’affichage de la page du document à imprimer en assignant une valeur au `m_nCurPage` membre de `CPrintInfo` ; la classe de vue récupère la valeur et effectue l’impression réelle de la page spécifiée.

Un autre exemple est le cas où la longueur du document n’est pas connue jusqu’à ce qu’il soit imprimé. Dans ce cas, la classe d’affichage teste la fin du document chaque fois qu’une page est imprimée. Lorsque la fin est atteinte, la classe d’affichage affecte la `m_bContinuePrinting` `CPrintInfo` valeur false au membre ; cela indique au Framework d’arrêter la boucle d’impression.

`CPrintInfo` est utilisé par les fonctions membres de `CView` listées sous « Voir aussi ». Pour plus d’informations sur l’architecture d’impression fournie par le bibliothèque MFC (Microsoft Foundation Class), consultez [Windows Frame](../../mfc/frame-windows.md) et [architecture document/vue](../../mfc/document-view-architecture.md) et les articles [impression](../../mfc/printing.md) et [impression : documents multipages](../../mfc/multipage-documents.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CPrintInfo`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="cprintinfogetfrompage"></a><a name="getfrompage"></a> CPrintInfo :: GetFromPage

Appelez cette fonction pour récupérer le numéro de la première page à imprimer.

```
UINT GetFromPage() const;
```

### <a name="return-value"></a>Valeur renvoyée

Numéro de la première page à imprimer.

### <a name="remarks"></a>Notes

Il s’agit de la valeur spécifiée par l’utilisateur dans la boîte de dialogue Imprimer, et elle est stockée dans l' `CPrintDialog` objet référencé par le `m_pPD` membre. Si l’utilisateur n’a pas spécifié de valeur, la valeur par défaut est la première page du document.

## <a name="cprintinfogetmaxpage"></a><a name="getmaxpage"></a> CPrintInfo :: GetMaxPage

Appelez cette fonction pour récupérer le numéro de la dernière page du document.

```
UINT GetMaxPage() const;
```

### <a name="return-value"></a>Valeur renvoyée

Numéro de la dernière page du document.

### <a name="remarks"></a>Notes

Cette valeur est stockée dans l' `CPrintDialog` objet référencé par le `m_pPD` membre.

## <a name="cprintinfogetminpage"></a><a name="getminpage"></a> CPrintInfo :: GetMinPage

Appelez cette fonction pour récupérer le numéro de la première page du document.

```
UINT GetMinPage() const;
```

### <a name="return-value"></a>Valeur renvoyée

Numéro de la première page du document.

### <a name="remarks"></a>Notes

Cette valeur est stockée dans l' `CPrintDialog` objet référencé par le `m_pPD` membre.

## <a name="cprintinfogetoffsetpage"></a><a name="getoffsetpage"></a> CPrintInfo :: GetOffsetPage

Appelez cette fonction pour récupérer le décalage lors de l’impression de plusieurs éléments DocObject à partir d’un client DocObject.

```
UINT GetOffsetPage() const;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre de pages précédant la première page d’un élément DocObject en cours d’impression dans un travail d’impression de DocObject combiné.

### <a name="remarks"></a>Notes

Cette valeur est référencée par le `m_nOffsetPage` membre. La première page de votre document sera numérotée à l' `m_nOffsetPage` aide de la valeur + 1 lors de l’impression en tant que DocObject avec d’autres documents actifs. Le `m_nOffsetPage` membre est valide uniquement si la `m_bDocObject` valeur est true.

## <a name="cprintinfogettopage"></a><a name="gettopage"></a> CPrintInfo :: GetToPage

Appelez cette fonction pour récupérer le numéro de la dernière page à imprimer.

```
UINT GetToPage() const;
```

### <a name="return-value"></a>Valeur renvoyée

Numéro de la dernière page à imprimer.

### <a name="remarks"></a>Notes

Il s’agit de la valeur spécifiée par l’utilisateur dans la boîte de dialogue Imprimer, et elle est stockée dans l' `CPrintDialog` objet référencé par le `m_pPD` membre. Si l’utilisateur n’a pas spécifié de valeur, la valeur par défaut est la dernière page du document.

## <a name="cprintinfom_bcontinueprinting"></a><a name="m_bcontinueprinting"></a> CPrintInfo :: m_bContinuePrinting

Contient un indicateur qui spécifie si l’infrastructure doit continuer la boucle d’impression.

### <a name="remarks"></a>Notes

Si vous effectuez une pagination au moment de l’impression, vous pouvez affecter à ce membre la valeur FALSe dans votre remplacement de `CView::OnPrepareDC` une fois que la fin du document a été atteinte. Vous n’avez pas besoin de modifier cette variable si vous avez spécifié la longueur du document au début du travail d’impression à l’aide de la `SetMaxPage` fonction membre. Le `m_bContinuePrinting` membre est une variable publique de type bool.

## <a name="cprintinfom_bdirect"></a><a name="m_bdirect"></a> CPrintInfo :: m_bDirect

L’infrastructure définit ce membre sur TRUE si la boîte de dialogue Imprimer est ignorée pour l’impression directe ; FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

La boîte de dialogue Imprimer est normalement ignorée lorsque vous imprimez à partir de l’interpréteur de commandes ou lorsque l’impression est effectuée à l’aide de l’ID de commande ID_FILE_PRINT_DIRECT.

Normalement, vous ne modifiez pas ce membre, mais si vous le modifiez, vous devez le modifier avant d’appeler [CView ::D oprepareprinting](../../mfc/reference/cview-class.md#doprepareprinting) dans votre remplacement de [CView :: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfom_bdocobject"></a><a name="m_bdocobject"></a> CPrintInfo :: m_bDocObject

Contient un indicateur qui spécifie si le document en cours d’impression est un DocObject.

### <a name="remarks"></a>Notes

Les membres `m_dwFlags` de données et `m_nOffsetPage` ne sont pas valides, sauf si cet indicateur a la valeur true.

## <a name="cprintinfom_bpreview"></a><a name="m_bpreview"></a> CPrintInfo :: m_bPreview

Contient un indicateur qui spécifie si l’aperçu du document est en cours.

### <a name="remarks"></a>Notes

Cela est défini par l’infrastructure en fonction de la commande exécutée par l’utilisateur. La boîte de dialogue Imprimer ne s’affiche pas pour un travail d’aperçu avant impression. Le `m_bPreview` membre est une variable publique de type bool.

## <a name="cprintinfom_dwflags"></a><a name="m_dwflags"></a> CPrintInfo :: m_dwFlags

Contient une combinaison d’indicateurs spécifiant les opérations d’impression DocObject.

### <a name="remarks"></a>Notes

Valide uniquement si le membre de données `m_bDocObject` a la valeur true.

Les indicateurs peuvent être une ou plusieurs des valeurs suivantes :

- PRINTFLAG_MAYBOTHERUSER

- PRINTFLAG_PROMPTUSER

- PRINTFLAG_USERMAYCHANGEPRINTER

- PRINTFLAG_RECOMPOSETODEVICE

- PRINTFLAG_DONTACTUALLYPRINT

- PRINTFLAG_FORCEPROPERTIES

- PRINTFLAG_PRINTTOFILE

## <a name="cprintinfom_lpuserdata"></a><a name="m_lpuserdata"></a> CPrintInfo :: m_lpUserData

Contient un pointeur vers une structure créée par l’utilisateur.

### <a name="remarks"></a>Notes

Vous pouvez l’utiliser pour stocker des données spécifiques à l’impression que vous ne souhaitez pas stocker dans votre classe d’affichage. Le `m_lpUserData` membre est une variable publique de type LPVOID.

## <a name="cprintinfom_ncurpage"></a><a name="m_ncurpage"></a> CPrintInfo :: m_nCurPage

Contient le numéro de la page actuelle.

### <a name="remarks"></a>Notes

Le Framework appelle `CView::OnPrepareDC` et `CView::OnPrint` une fois pour chaque page du document, en spécifiant à chaque fois une valeur différente pour ce membre ; ses valeurs sont comprises entre la valeur retournée par `GetFromPage` et celle retournée par `GetToPage` . Utilisez ce membre dans vos remplacements de `CView::OnPrepareDC` et `CView::OnPrint` pour imprimer la page spécifiée du document.

Lorsque le mode aperçu est appelé pour la première fois, le Framework lit la valeur de ce membre pour déterminer quelle page du document doit être prévisualisée initialement. Vous pouvez définir la valeur de ce membre dans votre remplacement de `CView::OnPreparePrinting` pour maintenir la position actuelle de l’utilisateur dans le document lors de l’entrée en mode aperçu. Le `m_nCurPage` membre est une variable publique de type uint.

## <a name="cprintinfom_njobnumber"></a><a name="m_njobnumber"></a> CPrintInfo :: m_nJobNumber

Indique le numéro de travail attribué par le système d’exploitation pour le travail d’impression en cours.

### <a name="remarks"></a>Notes

Cette valeur peut être SP_ERROR si le travail n’a pas encore été imprimé (autrement dit, si l' `CPrintInfo` objet est créé et n’a pas encore été utilisé pour l’impression) ou si une erreur s’est produite lors du démarrage du travail.

## <a name="cprintinfom_nnumpreviewpages"></a><a name="m_nnumpreviewpages"></a> CPrintInfo :: m_nNumPreviewPages

Contient le nombre de pages affichées en mode aperçu ; Il peut s’agir de la valeur 1 ou 2.

### <a name="remarks"></a>Notes

Le `m_nNumPreviewPages` membre est une variable publique de type uint.

## <a name="cprintinfom_noffsetpage"></a><a name="m_noffsetpage"></a> CPrintInfo :: m_nOffsetPage

Contient le nombre de pages précédant la première page d’un DocObject particulier dans un travail d’impression combiné DocObject.

## <a name="cprintinfom_ppd"></a><a name="m_ppd"></a> CPrintInfo :: m_pPD

Contient un pointeur vers l' `CPrintDialog` objet utilisé pour afficher la boîte de dialogue Imprimer pour le travail d’impression.

### <a name="remarks"></a>Notes

Le `m_pPD` membre est une variable publique déclarée comme pointeur vers `CPrintDialog` .

## <a name="cprintinfom_rectdraw"></a><a name="m_rectdraw"></a> CPrintInfo :: m_rectDraw

Spécifie la zone de dessin utilisable de la page en coordonnées logiques.

### <a name="remarks"></a>Notes

Vous pouvez vous y référer dans votre remplacement de `CView::OnPrint` . Vous pouvez utiliser ce membre pour effectuer le suivi de la zone qui reste utilisable après l’impression des en-têtes, des pieds de page, etc. Le `m_rectDraw` membre est une variable publique de type `CRect` .

## <a name="cprintinfom_strpagedesc"></a><a name="m_strpagedesc"></a> CPrintInfo :: m_strPageDesc

Contient une chaîne de format utilisée pour afficher les numéros de page lors de l’aperçu avant impression ; Cette chaîne se compose de deux sous-chaînes, l’une pour l’affichage d’une seule page et l’autre pour l’affichage de la double page, chacune terminée par un caractère « \n ».

### <a name="remarks"></a>Notes

L’infrastructure utilise « page%u\nPages% u-%u\n » comme valeur par défaut. Si vous souhaitez un format différent pour les numéros de page, spécifiez une chaîne de format dans votre remplacement de `CView::OnPreparePrinting` . Le `m_strPageDesc` membre est une variable publique de type `CString` .

## <a name="cprintinfosetmaxpage"></a><a name="setmaxpage"></a> CPrintInfo :: SetMaxPage

Appelez cette fonction pour spécifier le numéro de la dernière page du document.

```cpp
void SetMaxPage(UINT nMaxPage);
```

### <a name="parameters"></a>Paramètres

*nMaxPage*<br/>
Numéro de la dernière page du document.

### <a name="remarks"></a>Notes

Cette valeur est stockée dans l' `CPrintDialog` objet référencé par le `m_pPD` membre. Si la longueur du document est connue avant son impression, appelez cette fonction à partir de votre remplacement de `CView::OnPreparePrinting` . Si la longueur du document dépend d’un paramètre spécifié par l’utilisateur dans la boîte de dialogue Imprimer, appelez cette fonction à partir de votre remplacement de `CView::OnBeginPrinting` . Si la longueur du document n’est pas connue jusqu’à ce qu’il soit imprimé, utilisez le `m_bContinuePrinting` membre pour contrôler la boucle d’impression.

### <a name="example"></a>Exemple

  Consultez l’exemple pour [CView :: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting).

## <a name="cprintinfosetminpage"></a><a name="setminpage"></a> CPrintInfo :: SetMinPage

Appelez cette fonction pour spécifier le numéro de la première page du document.

```cpp
void SetMinPage(UINT nMinPage);
```

### <a name="parameters"></a>Paramètres

*nMinPage*<br/>
Numéro de la première page du document.

### <a name="remarks"></a>Notes

Les numéros de page commencent normalement à 1. Cette valeur est stockée dans l' `CPrintDialog` objet référencé par le `m_pPD` membre.

## <a name="see-also"></a>Voir aussi

[Exemple MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)<br/>
[CView :: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting)<br/>
[CView :: OnEndPrintPreview](../../mfc/reference/cview-class.md#onendprintpreview)<br/>
[CView :: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)<br/>
[CView :: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting)<br/>
[CView :: OnPrint](../../mfc/reference/cview-class.md#onprint)
