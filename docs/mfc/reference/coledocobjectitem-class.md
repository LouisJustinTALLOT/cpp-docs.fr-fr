---
title: Classe COleDocObjectItem
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
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375052"
---
# <a name="coledocobjectitem-class"></a>Classe COleDocObjectItem

Implémente la relation contenant-contenu de document actif.

## <a name="syntax"></a>Syntaxe

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Construit un `COleDocObject` article.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Imprime le document de l’application du conteneur à l’aide des paramètres de l’imprimante par défaut.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Exécute la commande spécifiée par l’utilisateur.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Récupère la vue active du document.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Récupère le nombre de pages dans le document de l’application de conteneurs.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Prépare le document de l’application de conteneurs pour l’impression.|
|[COleDocObjectItem::OnPrint](#onprint)|Imprime le document de l’application du conteneur.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Demande l’état d’une ou plusieurs commandes générées par des événements d’interface utilisateur.|
|[COleDocObjectItem::Libération](#release)|Communiqués de connexion à un élément lié à l’OLE et le ferme s’il était ouvert. Ne détruit pas l’article du client.|

## <a name="remarks"></a>Notes

Dans MFC, un document Actif est traité de la même façon qu’un embécrétable régulier et en place, avec les différences suivantes :

- La `COleDocument`classe dérivée tient toujours une liste des éléments actuellement intégrés; toutefois, ces éléments `COleDocObjectItem`peuvent être des éléments dérivés.

- Lorsqu’un document actif est actif, il occupe toute la zone client de la vue lorsqu’il est actif sur place.

- Un conteneur de documents actifs a le plein contrôle du menu **Aide.**

- Le menu **Help** contient des éléments de menu pour le conteneur de documents actif et le serveur.

Étant donné que le conteneur de documents Active est propriétaire du menu **Aide,** le conteneur est responsable de l’expédition des messages de menu **d’aide** au serveur. Cette intégration est `COleDocObjectItem`gérée par .

Pour plus d’informations sur la fusion du menu et l’activation active des documents, voir Aperçu du [confinement actif des documents](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem

Appelez cette fonction de `COleDocObjectItem` membre pour initialiser l’objet.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Paramètres

*pContainerDoc*<br/>
Un pointeur `COleDocument` de l’objet agissant comme le conteneur de documents actif. Ce paramètre doit être NULL pour permettre IMPLEMENT_SERIALIZE. Normalement, les éléments OLE sont construits avec un pointeur de document non-NULL.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting

Appelé par le cadre à un document en utilisant les paramètres par défaut.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pCaller (en)*<br/>
Un pointeur vers un objet [CView](../../mfc/reference/cview-class.md) qui envoie la commande d’impression.

*pInfo (en anglais)*<br/>
Un pointeur d’un objet [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail à imprimer.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObjectItem::ExecCommand

Appelez cette fonction de membre pour exécuter la commande spécifiée par l’utilisateur.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Paramètres

*nCmdID (en)*<br/>
L’identifiant de la commande à exécuter. Doit faire dans le groupe identifié par *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Spécifie les options d’exécution de commande. Par défaut, définissez pour exécuter la commande sans inciter l’utilisateur. Consultez [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) pour une liste de valeurs.

*pguidCmdGroup*<br/>
Identificateur unique du groupe de commandes. Par défaut, NULL, qui spécifie le groupe standard. Le commandement passé en *nCmdID* doit appartenir au groupe.

### <a name="return-value"></a>Valeur de retour

Retours S_OK en cas de succès; sinon, retourne l’un des codes d’erreur suivants.

|Valeur|Description|
|-----------|-----------------|
|E_UNEXPECTED|Une erreur inattendue s'est produite.|
|E_FAIL|Une erreur s’est produite.|
|E_NOTIMPL|Indique que MFC lui-même devrait tenter de traduire et d’envoyer la commande.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* n’est pas NULL mais ne précise pas un groupe de commandement reconnu.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* n’est pas reconnu comme une commande valide dans le groupe pGroup.|
|OLECMDERR_DISABLED|La commande identifiée par *nCmdID* est désactivée et ne peut pas être exécutée.|
|OLECMDERR_NOHELP|L’appelant a demandé de l’aide sur la commande identifiée par *nCmdID,* mais aucune aide n’est disponible.|
|OLECMDERR_CANCELLED|L’utilisateur a annulé l’exécution.|

### <a name="remarks"></a>Notes

Le *pguidCmdGroup* et les paramètres *nCmdID* identifient de manière unique la commande à invoquer. Le *paramètre nCmdExecOpt* spécifie l’action exacte à prendre.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDocObjectItem::GetActiveView

Appelez cette fonction de membre `IOleDocumentView` pour obtenir un pointeur à l’interface de la vue actuellement active.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à l’interface [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) de la vue actuellement active. S’il n’y a pas de vue actuelle, il renvoie NULL.

### <a name="remarks"></a>Notes

Le compte de `IOleDocumentView` référence sur le pointeur retourné n’est pas incrémenté avant qu’il ne soit retourné par cette fonction.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDocObjectItem::GetPageCount

Appelez cette fonction de membre pour récupérer le nombre de pages dans le document.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Paramètres

*pnFirstPage (en)*<br/>
Un pointeur sur le numéro de la première page du document. Peut être NULL, ce qui indique que l’appelant n’a pas besoin de ce numéro.

*pcPages*<br/>
Un pointeur sur le nombre total de pages du document. Peut être NULL, ce qui indique que l’appelant n’a pas besoin de ce numéro.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting

Cette fonction de membre est appelée par le cadre pour préparer un document pour l’impression.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pCaller (en)*<br/>
Un pointeur vers un objet [CView](../../mfc/reference/cview-class.md) qui envoie la commande d’impression.

*pInfo (en anglais)*<br/>
Un pointeur d’un objet [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail à imprimer.

*bPrintAll (en)*<br/>
Précise si l’ensemble du document doit être imprimé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObjectItem::OnPrint

Cette fonction de membre est appelée par le cadre pour imprimer un document.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Paramètres

*pCaller (en)*<br/>
Un pointeur vers un objet CView qui envoie la commande d’impression.

*pInfo (en anglais)*<br/>
Un pointeur d’un objet [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail à imprimer.

*bPrintAll (en)*<br/>
Précise si l’ensemble du document doit être imprimé.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDocObjectItem::QueryCommand

Demande l’état d’une ou plusieurs commandes générées par des événements d’interface utilisateur.

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>Paramètres

*nCmdID (en)*<br/>
l’identification de la commande demandée.

*pdwStatus*<br/>
Un pointeur pour les drapeaux est revenu à la suite de la requête. Pour une liste de valeurs possibles, voir [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Pointeur vers une structure [OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext) dans laquelle retourner les informations de nom et d’état pour une seule commande. Peut être NULL pour indiquer que l’appelant n’a pas besoin de cette information.

*pguidCmdGroup*<br/>
Identifiant unique du groupe de commandement; peut être NULL pour spécifier le groupe standard.

### <a name="return-value"></a>Valeur de retour

Pour une liste complète des valeurs de retour, voir [IOleCommandTarget:QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) dans le SDK Windows.

### <a name="remarks"></a>Notes

Cette fonction de membre imite la fonctionnalité de la méthode [IOleCommandTarget::QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) méthode, comme décrit dans le SDK Windows.

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObjectItem::Libération

Communiqués de connexion à un élément lié à l’OLE et le ferme s’il était ouvert. Ne détruit pas l’article du client.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Paramètres

*dwCloseOption*<br/>
Indicateur spécifiant dans quelles circonstances l’élément OLE est enregistré lorsqu’il retourne à l’état chargé. Pour une liste de valeurs possibles, voir [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Notes

Ne détruit pas l’article du client.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[Classe COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem, classe](../../mfc/reference/cdocobjectserveritem-class.md)
