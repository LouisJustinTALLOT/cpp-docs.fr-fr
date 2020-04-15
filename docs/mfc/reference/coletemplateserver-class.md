---
title: COleTemplateServer, classe
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: ddd7a8ce70fe49e66e1175e413418fd59a89c917
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374851"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer, classe

Utilisée pour les serveurs d'édition visuelle OLE, les serveurs Automation et les conteneurs de lien (applications qui prennent en charge les liaisons aux incorporations).

## <a name="syntax"></a>Syntaxe

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Construit un objet `COleTemplateServer`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Connecte un modèle de `COleObjectFactory` document à l’objet sous-jacent.|
|[COleTemplateServer::Unregister](#unregister)|Désenregistre le modèle de document associé.|
|[COleTemplateServer::Mise à jourRegistry](#updateregistry)|Enregistre le type de document avec le registre du système OLE.|

## <a name="remarks"></a>Notes

Cette classe est dérivée de la classe [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); habituellement, vous `COleTemplateServer` pouvez utiliser directement plutôt que de dérivant votre propre classe. `COleTemplateServer`utilise un objet [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) pour gérer les documents du serveur. Utilisez `COleTemplateServer` lors de la mise en œuvre d’un serveur complet, c’est-à-dire un serveur qui peut être exécuté comme une application autonome. Les serveurs complets sont généralement plusieurs applications d’interface documentaire (MDI), bien que les applications d’interface de document unique (SDI) soient prises en charge. Un `COleTemplateServer` objet est nécessaire pour chaque type de document serveur qu’une application prend en charge ; c’est-à-dire que si votre application serveur prend `COleTemplateServer` en charge à la fois les feuilles de travail et les graphiques, vous devez avoir deux objets.

`COleTemplateServer`remplace la `OnCreateInstance` fonction membre `COleObjectFactory`définie par . Cette fonction de membre est appelée par le cadre pour créer un objet C de type approprié.

Pour plus d’informations sur les serveurs, voir l’article [Serveurs: Implémenter un serveur](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer

Construit un objet `COleTemplateServer`.

```
COleTemplateServer();
```

### <a name="remarks"></a>Notes

Pour une brève description de `COleTemplateServer` l’utilisation de la classe, consultez la vue d’ensemble de la classe [COleLinkingDoc.](../../mfc/reference/colelinkingdoc-class.md)

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate

Connecte le modèle de document pointé par *pDocTemplate* à l’objet [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) sous-jacent.

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
Référence à l’ID de classe OLE que le modèle demande.

*pDocTemplate (en)*<br/>
Pointeur vers le modèle de document.

*bMultiInstance*<br/>
Indique si une seule instance de l’application peut prendre en charge plusieurs instantanés. Si VRAI, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplateServer::Unregister

Désenregistre le modèle de document associé.

```
BOOL Unregister();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

EntrezRemarks

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplateServer::Mise à jourRegistry

Charge les informations de type fichier à partir de la chaîne de modèle de document et place ces informations dans le registre du système OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Paramètres

*nAppType (en)*<br/>
Une valeur de l’énumération OLE_APPTYPE, qui est définie dans AFXDISP. H. Il peut avoir l’une des valeurs suivantes:

- OAT_INPLACE_SERVER Server dispose d’une interface utilisateur-utilisateur complète.

- OAT_SERVER Server ne prend en charge que l’intégration.

- OAT_CONTAINER Container prend en charge les liens vers des objets embarqués.

- OAT_DISPATCH_OBJECT’objet est `IDispatch`capable.

- OAT_DOC_OBJECT_SERVER Server prend en charge à la fois l’intégration et le modèle de composant d’objet document.

*rglpszRegister (rglpszRegister)*<br/>
Une liste d’entrées qui n’est inscrite dans le registre que si aucune inscription n’existe.

*rglpszOverwrite*<br/>
Une liste d’inscriptions inscrites dans le registre, qu’il existe ou non des inscriptions précédentes.

*bRegister (en)*<br/>
Détermine si la classe doit être enregistrée. Si *bRegister* est VRAI, la classe est enregistrée auprès du registre du système. Sinon, il ne s’inscrit pas à la classe.

### <a name="remarks"></a>Notes

Les informations d’enregistrement sont chargées au moyen d’un appel à [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Les sous-cordes récupérées sont celles `regFileTypeId`identifiées `regFileTypeName`par `fileNewName`les index `GetDocString` , et , comme décrit dans les pages de référence.

Si `regFileTypeId` la sous-corde est vide `GetDocString` ou si l’appel échoue pour une autre raison, cette fonction échoue et les informations du fichier ne sont pas saisies dans le registre.

Les informations contenues dans les arguments *rglpszRegister* et *rglpszOverwrite* sont écrites au registre par le biais d’un appel à [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Les informations par défaut, qui sont enregistrées lorsque les deux arguments sont NULL, conviennent à la plupart des applications. Pour plus d’informations sur la structure `AfxOleRegisterServerClass`de l’information dans ces arguments, voir .

Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory, classe](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
