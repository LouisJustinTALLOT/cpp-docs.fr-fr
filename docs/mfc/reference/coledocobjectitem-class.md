---
title: Classe COleDocObjectItem | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af2b13b8da5f70cf55b47ddf3b7864f9f9151a40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
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
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Construit un `COleDocObject` élément.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Imprime le document de l’application conteneur en utilisant les paramètres d’imprimante par défaut.|  
|[COleDocObjectItem::ExecCommand](#execcommand)|Exécute la commande spécifiée par l’utilisateur.|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|Récupère le mode du document actif.|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|Récupère le nombre de pages dans le document de l’application conteneur.|  
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Prépare le document de l’application conteneur pour l’impression.|  
|[COleDocObjectItem::OnPrint](#onprint)|Imprime le document de l’application conteneur.|  
|[COleDocObjectItem::QueryCommand](#querycommand)|Demande l’état d’une ou plusieurs commandes générées par des événements d’interface utilisateur.|  
|[COleDocObjectItem::Release](#release)|Libère la connexion à l’élément lié OLE et la ferme s’il est ouvert. Ne supprime pas l’élément client.|  
  
## <a name="remarks"></a>Notes  
 Dans les MFC, un document actif est géré de façon analogue à une réguliers, in situ modifiable l’incorporation, avec les différences suivantes :  
  
-   Le `COleDocument`-classe dérivée conserve une liste des éléments actuellement incorporés ; Toutefois, ces éléments peuvent être `COleDocObjectItem`-éléments dérivés.  
  
-   Lorsqu’un document actif est actif, elle occupe la zone cliente de la vue lorsqu’il est actif en place.  
  
-   Un conteneur de documents actifs a le contrôle total sur le **aide** menu.  
  
-   Le **aide** menu contient des éléments de menu pour le conteneur de documents actifs et le serveur.  
  
 Étant donné que le conteneur de document actif possède le **aide** menu, le conteneur est responsable du serveur de transfert **aide** messages de menu au serveur. Cette intégration est gérée par `COleDocObjectItem`.  
  
 Pour plus d’informations sur la fusion de menus et de l’activation de document actif, consultez Vue d’ensemble de [relation contenant-contenu de Document actif](../../mfc/active-document-containment.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxole.h  
  
##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem  
 Appelez cette fonction membre pour initialiser le `COleDocObjectItem` objet.  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pContainerDoc`  
 Un pointeur vers le `COleDocument` objet agissant en tant que le conteneur de documents actifs. Ce paramètre doit être **NULL** pour activer **IMPLEMENT_SERIALIZE**. Normalement les éléments OLE sont construits avec un non - **NULL** pointeur de document.  
  
##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting  
 Appelé par l’infrastructure à un document en utilisant les paramètres par défaut.  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCaller`  
 Un pointeur vers un [CView](../../mfc/reference/cview-class.md) objet qui envoie la commande d’impression.  
  
 `pInfo`  
 Un pointeur vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objet qui décrit le travail d’impression.  
  
##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand  
 Appelez cette fonction membre pour exécuter la commande spécifiée par l’utilisateur.  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nCmdID`  
 Identificateur de la commande à exécuter. Doit être dans le groupe identifié par `pguidCmdGroup`.  
  
 `nCmdExecOpt`  
 Spécifie les options de commande en cours d’exécution. Par défaut, la valeur pour exécuter la commande sans solliciter l’utilisateur. Consultez [OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930) pour obtenir la liste de valeurs.  
  
 `pguidCmdGroup`  
 Identificateur unique du groupe de commandes. Par défaut, **NULL**, qui spécifie le groupe standard. La commande passée dans `nCmdID` doit appartenir au groupe.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite ; sinon, retourne un des codes d’erreur suivants.  
  
|Value|Description|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Une erreur inattendue s’est produite.|  
|**E_FAIL**|Erreur s’est produite.|  
|**E_NOTIMPL**|Indique les MFC elle-même doit tenter de traduction et de distribuer la commande.|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup` est non - **NULL** mais ne spécifie ne pas un groupe de commandes reconnu.|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID` n’est pas reconnu comme une commande valide dans le groupe pGroup.|  
|**OLECMDERR_DISABLED**|La commande identifiée par `nCmdID` est désactivé et ne peut pas être exécutée.|  
|**OLECMDERR_NOHELP**|L’appelant a demandé de l’aide sur la commande identifiée par `nCmdID` mais aucune aide n’est disponible.|  
|**OLECMDERR_CANCELLED**|L’utilisateur a annulé l’exécution.|  
  
### <a name="remarks"></a>Notes  
 Le `pguidCmdGroup` et `nCmdID` paramètres identifier de façon unique la commande à appeler. Le `nCmdExecOpt` paramètre spécifie l’action exacte à appliquer.  
  
##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView  
 Appelez cette fonction membre pour obtenir un pointeur vers le `IOleDocumentView` interface de la vue actuellement active.  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le [IOleDocumentView](http://msdn.microsoft.com/library/windows/desktop/ms678455) interface de la vue actuellement active. S’il n’existe aucun affichage actuel, elle retourne **NULL**.  
  
### <a name="remarks"></a>Notes  
 Le décompte de références sur le `IOleDocumentView` pointeur n’est pas incrémenté avant d’être retournée par cette fonction.  
  
##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount  
 Appelez cette fonction membre pour récupérer le nombre de pages dans le document.  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>Paramètres  
 *pnFirstPage*  
 Pointeur vers le nombre de la page du document première. Peut être **NULL**, ce qui indique à l’appelant n’a pas besoin de ce numéro.  
  
 *pcPages*  
 Pointeur vers le nombre total de pages dans le document. Peut être **NULL**, ce qui indique à l’appelant n’a pas besoin de ce numéro.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting  
 Cette fonction membre est appelée par l’infrastructure pour préparer un document pour l’impression.  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCaller`  
 Un pointeur vers un [CView](../../mfc/reference/cview-class.md) objet qui envoie la commande d’impression.  
  
 `pInfo`  
 Un pointeur vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objet qui décrit le travail d’impression.  
  
 `bPrintAll`  
 Spécifie si l’ensemble du document doit être imprimé.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
##  <a name="onprint"></a>  COleDocObjectItem::OnPrint  
 Cette fonction membre est appelée par l’infrastructure pour imprimer un document.  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pCaller`  
 Pointeur vers un objet de CView qui envoie la commande d’impression.  
  
 `pInfo`  
 Un pointeur vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objet qui décrit le travail d’impression.  
  
 `bPrintAll`  
 Spécifie si l’ensemble du document doit être imprimé.  
  
##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand  
 Demande l’état d’une ou plusieurs commandes générées par des événements d’interface utilisateur.  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `nCmdID`  
 identificateur de la commande en cours d’interrogation.  
  
 `pdwStatus`  
 Pointeur vers les indicateurs retournés à la suite de la requête. Pour obtenir la liste des valeurs possibles, consultez [OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237).  
  
 `pCmdText`  
 Pointeur vers un [OLECMDTEXT](http://msdn.microsoft.com/library/windows/desktop/ms693314) structure dans laquelle retourner des informations de nom et l’état d’une commande unique. Peut être **NULL** pour indiquer que l’appelant ne doit pas ces informations.  
  
 `pguidCmdGroup`  
 Identificateur unique du groupe de commandes ; peut être **NULL** pour spécifier le groupe standard.  
  
### <a name="return-value"></a>Valeur de retour  
 Pour obtenir une liste complète des valeurs de retour, consultez [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) dans le Kit de développement logiciel Windows.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) (méthode), comme décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="release"></a>  COleDocObjectItem::Release  
 Libère la connexion à l’élément lié OLE et la ferme s’il est ouvert. Ne supprime pas l’élément client.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Paramètres  
 `dwCloseOption`  
 Indicateur spécifiant dans quelles circonstances l’élément OLE est enregistrée lorsqu’il retourne à l’état chargé. Pour obtenir la liste des valeurs possibles, consultez [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).  
  
### <a name="remarks"></a>Notes  
 Ne supprime pas l’élément client.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC MFCBIND](../../visual-cpp-samples.md)   
 [Classe de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classe de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem, classe](../../mfc/reference/cdocobjectserveritem-class.md)
