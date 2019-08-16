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
ms.openlocfilehash: 4a1997497f3bddb405b712b5534f76e577dabfa8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503091"
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
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Connecte un modèle de document à `COleObjectFactory` l’objet sous-jacent.|
|[COleTemplateServer::Unregister](#unregister)|Annule l’inscription du modèle de document associé.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Inscrit le type de document auprès du Registre système OLE.|

## <a name="remarks"></a>Notes

Cette classe est dérivée de la classe [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); en règle générale, vous `COleTemplateServer` pouvez utiliser directement plutôt que de dériver votre propre classe. `COleTemplateServer`utilise un objet [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) pour gérer les documents du serveur. À `COleTemplateServer` utiliser lors de l’implémentation d’un serveur complet, autrement dit, un serveur qui peut être exécuté en tant qu’application autonome. Les serveurs complets sont généralement des applications d’interface multidocument (MDI, multiple document interface), bien que les applications SDI (single document interface) soient prises en charge. Un `COleTemplateServer` objet est nécessaire pour chaque type de document serveur pris en charge par une application; autrement dit, si votre application serveur prend en charge les feuilles de calcul et `COleTemplateServer` les graphiques, vous devez disposer de deux objets.

`COleTemplateServer`remplace la `OnCreateInstance` fonction membre définie par `COleObjectFactory`. Cette fonction membre est appelée par l’infrastructure pour créer un C++ objet du type approprié.

Pour plus d’informations sur les serveurs, consultez [l’article serveurs: Implémentation d’un](../../mfc/servers-implementing-a-server.md)serveur.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer

Construit un objet `COleTemplateServer`.

```
COleTemplateServer();
```

### <a name="remarks"></a>Notes

Pour obtenir une brève description de l’utilisation de `COleTemplateServer` la classe, consultez la vue d’ensemble de la classe [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) .

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

Connecte le modèle de document pointé par *pDocTemplate* à l’objet [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) sous-jacent.

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
Référence à l’ID de classe OLE demandé par le modèle.

*pDocTemplate*<br/>
Pointeur vers le modèle de document.

*bMultiInstance*<br/>
Indique si une seule instance de l’application peut prendre en charge plusieurs instanciations. Si la valeur est TRUE, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [clé CLSID](/windows/win32/com/clsid-key-hklm) dans le SDK Windows.

##  <a name="unregister"></a>  COleTemplateServer::Unregister

Annule l’inscription du modèle de document associé.

```
BOOL Unregister();
```

### <a name="return-value"></a>Valeur de retour

TRUE en cas de réussite, sinon FALSE.

### <a name="remarks"></a>Notes

EnterRemarks

##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry

Charge les informations de type de fichier à partir de la chaîne de modèle de document et place ces informations dans le registre système OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Paramètres

*nAppType*<br/>
Valeur de l’énumération OLE_APPTYPE, qui est définie dans AFXDISP. Manutention. Il peut avoir l’une des valeurs suivantes:

- Le serveur OAT_INPLACE_SERVER dispose de l’interface utilisateur complète du serveur.

- Le serveur OAT_SERVER prend uniquement en charge l’incorporation.

- Le conteneur OAT_CONTAINER prend en charge les liens vers les objets incorporés.

- L’objet OAT_DISPATCH_OBJECT `IDispatch`est apte à l’être.

- Le serveur OAT_DOC_OBJECT_SERVER prend en charge l’incorporation et le modèle de composant objet de document.

*rglpszRegister*<br/>
Liste des entrées écrites dans le registre uniquement si aucune entrée n’existe.

*rglpszOverwrite*<br/>
Liste des entrées écrites dans le registre, que toutes les entrées précédentes existent ou non.

*bRegister*<br/>
Détermine si la classe doit être inscrite. Si *bRegister* a la valeur true, la classe est inscrite auprès du Registre système. Dans le cas contraire, il annule l’inscription de la classe.

### <a name="remarks"></a>Notes

Les informations d’inscription sont chargées au moyen d’un appel à [CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Les sous-chaînes récupérées sont celles identifiées par les `regFileTypeId`index `regFileTypeName`, et `fileNewName`, comme décrit dans les `GetDocString` pages de référence.

Si la `regFileTypeId` sous-chaîne est vide ou si l’appel `GetDocString` à échoue pour une autre raison, cette fonction échoue et les informations du fichier ne sont pas entrées dans le registre.

Les informations des arguments *rglpszRegister* et *rglpszOverwrite* sont écrites dans le registre via un appel à [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Les informations par défaut, inscrites lorsque les deux arguments sont NULL, conviennent à la plupart des applications. Pour plus d’informations sur la structure des informations contenues dans ces `AfxOleRegisterServerClass`arguments, consultez.

Pour plus d'informations, consultez [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory, classe](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
