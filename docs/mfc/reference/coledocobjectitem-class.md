---
description: 'En savoir plus sur : COleDocObjectItem, classe'
title: COleDocObjectItem, classe
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: e483c614f8bc7558a827c51889bbffa7da7419b8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227219"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem, classe

Implémente la relation contenant-contenu de document actif.

## <a name="syntax"></a>Syntaxe

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDocObjectItem :: COleDocObjectItem](#coledocobjectitem)|Construit un `COleDocObject` élément.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDocObjectItem ::D oDefaultPrinting](#dodefaultprinting)|Imprime le document de l’application conteneur à l’aide des paramètres d’imprimante par défaut.|
|[COleDocObjectItem :: ExecCommand](#execcommand)|Exécute la commande spécifiée par l’utilisateur.|
|[COleDocObjectItem :: GetActiveView](#getactiveview)|Récupère la vue active du document.|
|[COleDocObjectItem :: GetPageCount](#getpagecount)|Récupère le nombre de pages dans le document de l’application conteneur.|
|[COleDocObjectItem :: OnPreparePrinting](#onprepareprinting)|Prépare le document de l’application conteneur pour l’impression.|
|[COleDocObjectItem :: OnPrint](#onprint)|Imprime le document de l’application conteneur.|
|[COleDocObjectItem :: QueryCommand](#querycommand)|Demande l’état d’une ou plusieurs commandes générées par des événements d’interface utilisateur.|
|[COleDocObjectItem :: Release](#release)|Libère la connexion à un élément lié OLE et la ferme si elle était ouverte. Ne détruit pas l’élément client.|

## <a name="remarks"></a>Notes

Dans MFC, un document actif est traité de la même manière qu’une incorporation modifiable sur place, avec les différences suivantes :

- La `COleDocument` classe dérivée de contient toujours une liste des éléments actuellement incorporés ; Toutefois, ces éléments peuvent être `COleDocObjectItem` des éléments dérivés de.

- Lorsqu’un document actif est actif, il occupe toute la zone cliente de la vue lorsqu’il est actif sur place.

- Un conteneur de documents actifs dispose du contrôle total du menu **aide** .

- Le menu **aide** contient des éléments de menu pour le conteneur et le serveur de documents actifs.

Étant donné que le conteneur de documents actifs possède le menu **aide** , le conteneur est chargé de transférer les messages du menu **aide** du serveur vers le serveur. Cette intégration est gérée par `COleDocObjectItem` .

Pour plus d’informations sur la fusion de menus et l’activation de documents actifs, consultez vue d’ensemble de la [relation contenant-contenu de document actif](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a> COleDocObjectItem :: COleDocObjectItem

Appelez cette fonction membre pour initialiser l' `COleDocObjectItem` objet.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Paramètres

*pContainerDoc*<br/>
Pointeur vers l' `COleDocument` objet agissant comme le conteneur de documents actifs. Ce paramètre doit avoir la valeur NULL pour permettre l’IMPLEMENT_SERIALIZE. Normalement, les éléments OLE sont construits avec un pointeur de document non NULL.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a> COleDocObjectItem ::D oDefaultPrinting

Appelée par l’infrastructure dans un document à l’aide des paramètres par défaut.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pCaller*<br/>
Pointeur vers un objet [CView](../../mfc/reference/cview-class.md) qui envoie la commande Imprimer.

*pInfo*<br/>
Pointeur vers un objet [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail à imprimer.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a> COleDocObjectItem :: ExecCommand

Appelez cette fonction membre pour exécuter la commande spécifiée par l’utilisateur.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*nCmdID*<br/>
Identificateur de la commande à exécuter. Doit se trouver dans le groupe identifié par *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Spécifie les options d’exécution de commande. Par défaut, définissez pour exécuter la commande sans inviter l’utilisateur. Pour obtenir la liste des valeurs, consultez [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) .

*pguidCmdGroup*<br/>
Identificateur unique du groupe de commandes. Par défaut, NULL, qui spécifie le groupe standard. La commande passée dans *nCmdId* doit appartenir au groupe.

### <a name="return-value"></a>Valeur renvoyée

Retourne S_OK en cas de réussite ; Sinon, retourne l’un des codes d’erreur suivants.

|Valeur|Description|
|-----------|-----------------|
|E_UNEXPECTED|Une erreur inattendue s'est produite.|
|E_FAIL|Une erreur s’est produite.|
|E_NOTIMPL|Indique que MFC lui-même doit tenter de traduire et de distribuer la commande.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* n’a pas la valeur null, mais ne spécifie pas de groupe de commandes reconnu.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdId* n’est pas reconnu en tant que commande valide dans le groupe pGroup.|
|OLECMDERR_DISABLED|La commande identifiée par *nCmdId* est désactivée et ne peut pas être exécutée.|
|OLECMDERR_NOHELP|L’appelant a demandé de l’aide sur la commande identifiée par *nCmdId* , mais aucune aide n’est disponible.|
|OLECMDERR_CANCELLED|L’utilisateur a annulé l’exécution.|

### <a name="remarks"></a>Notes

Les paramètres *pguidCmdGroup* et *nCmdId* identifient ensemble de façon unique la commande à appeler. Le paramètre *nCmdExecOpt* spécifie l’action exacte à entreprendre.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a> COleDocObjectItem :: GetActiveView

Appelez cette fonction membre pour obtenir un pointeur vers l' `IOleDocumentView` interface de la vue actuellement active.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers l’interface [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) de la vue actuellement active. S’il n’existe pas d’affichage actuel, la valeur NULL est retournée.

### <a name="remarks"></a>Notes

Le décompte de références sur le `IOleDocumentView` pointeur retourné n’est pas incrémenté avant d’être retourné par cette fonction.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a> COleDocObjectItem :: GetPageCount

Appelez cette fonction membre pour récupérer le nombre de pages dans le document.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Paramètres

*pnFirstPage*<br/>
Pointeur vers le numéro de la première page du document. Peut avoir la valeur NULL, ce qui indique que l’appelant n’a pas besoin de ce numéro.

*pcPages*<br/>
Pointeur vers le nombre total de pages dans le document. Peut avoir la valeur NULL, ce qui indique que l’appelant n’a pas besoin de ce numéro.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a> COleDocObjectItem :: OnPreparePrinting

Cette fonction membre est appelée par l’infrastructure pour préparer un document à l’impression.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pCaller*<br/>
Pointeur vers un objet [CView](../../mfc/reference/cview-class.md) qui envoie la commande Imprimer.

*pInfo*<br/>
Pointeur vers un objet [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail à imprimer.

*bPrintAll*<br/>
Spécifie si l’intégralité du document doit être imprimée.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a> COleDocObjectItem :: OnPrint

Cette fonction membre est appelée par l’infrastructure pour imprimer un document.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pCaller*<br/>
Pointeur vers un objet CView qui envoie la commande Imprimer.

*pInfo*<br/>
Pointeur vers un objet [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail à imprimer.

*bPrintAll*<br/>
Spécifie si l’intégralité du document doit être imprimée.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a> COleDocObjectItem :: QueryCommand

Demande l’état d’une ou plusieurs commandes générées par des événements d’interface utilisateur.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Paramètres

*nCmdID*<br/>
identificateur de la commande en cours d’interrogation.

*pdwStatus*<br/>
Pointeur vers les indicateurs retournés en tant que résultat de la requête. Pour obtenir la liste des valeurs possibles, consultez [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Pointeur vers une structure [OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext) dans laquelle retourner les informations de nom et d’État pour une seule commande. Peut avoir la valeur NULL pour indiquer que l’appelant n’a pas besoin de ces informations.

*pguidCmdGroup*<br/>
Identificateur unique du groupe de commandes ; peut avoir la valeur NULL pour spécifier le groupe standard.

### <a name="return-value"></a>Valeur renvoyée

Pour obtenir la liste complète des valeurs de retour, consultez [IOleCommandTarget :: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction membre émule les fonctionnalités de la méthode [IOleCommandTarget :: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) , comme décrit dans la SDK Windows.

## <a name="coledocobjectitemrelease"></a><a name="release"></a> COleDocObjectItem :: Release

Libère la connexion à un élément lié OLE et la ferme si elle était ouverte. Ne détruit pas l’élément client.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Paramètres

*dwCloseOption*<br/>
Indicateur spécifiant dans quelles circonstances l’élément OLE est enregistré lorsqu’il revient à l’État chargé. Pour obtenir la liste des valeurs possibles, consultez [COleClientItem :: Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Notes

Ne détruit pas l’élément client.

## <a name="see-also"></a>Voir aussi

[Exemple MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem (classe)](../../mfc/reference/coleclientitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem (classe)](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem, classe](../../mfc/reference/cdocobjectserveritem-class.md)
