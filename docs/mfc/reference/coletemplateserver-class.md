---
title: COleTemplateServer, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c77c8cc20588df8329951167db502a65a67b3756
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849338"
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
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Se connecte un modèle de document sous-jacent `COleObjectFactory` objet.|  
|[COleTemplateServer::Unregister](#unregister)|Annule l’inscription du modèle de document associé.|  
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Inscrit le type de document avec le Registre du système OLE.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est dérivée de la classe [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); en règle générale, vous pouvez utiliser `COleTemplateServer` directement au lieu de dériver votre propre classe. `COleTemplateServer` utilise un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objet pour gérer les documents de serveur. Utilisez `COleTemplateServer` lors de l’implémentation d’un serveur complet, autrement dit, un serveur qui peut être exécuté comme une application autonome. Serveurs complètes sont généralement plusieurs applications d’interface (multidocument MDI) document, bien que les applications SDI (interface) de document unique sont pris en charge. Un `COleTemplateServer` objet est nécessaire pour chaque type de document serveur prend en charge par une application ; autrement dit, si votre application serveur prend en charge les feuilles de calcul et graphiques, vous devez disposer de deux `COleTemplateServer` objets.  
  
 `COleTemplateServer` remplace le `OnCreateInstance` fonction membre définie par `COleObjectFactory`. Cette fonction membre est appelée par l’infrastructure pour créer un objet C++ du type approprié.  
  
 Pour plus d’informations sur les serveurs, consultez l’article [serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md).  
  
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
 Pour une brève description de l’utilisation de la `COleTemplateServer` de classe, consultez le [COleLinkingDoc plutôt](../../mfc/reference/colelinkingdoc-class.md) vue d’ensemble de la classe.  
  
##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate  
 Connecte le modèle de document vers lequel pointé *pDocTemplate* sous-jacentes [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) objet.  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>Paramètres  
 *clsid*  
 Référence à l’ID de classe OLE qui demande le modèle.  
  
 *pDocTemplate*  
 Pointeur vers le modèle de document.  
  
 *bMultiInstance*  
 Indique si une seule instance de l’application peut prendre en charge de plusieurs instanciations. Si la valeur est TRUE, plusieurs instances de l’application sont lancées pour chaque demande de création d’un objet.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [clé CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) dans le SDK Windows.  
  
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
 Charge des informations de type de fichier à partir de la chaîne de modèle de document et les place dans le Registre du système OLE.  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *nAppType*  
 Une valeur de l’énumération OLE_APPTYPE, qui est définie dans AFXDISP. H. Il peut avoir l’une des valeurs suivantes :  
  
- OAT_INPLACE_SERVER serveur a l’interface utilisateur complète du serveur.  
  
- OAT_SERVER Server prend en charge uniquement l’incorporation.  
  
- OAT_CONTAINER conteneur prend en charge des liens vers des objets incorporés.  
  
- Objet de OAT_DISPATCH_OBJECT est `IDispatch`-compatible.  
  
- OAT_DOC_OBJECT_SERVER Server prend en charge l’incorporation et le modèle de composant d’objet de Document.  
  
 *rglpszRegister*  
 Une liste d’entrées qui est écrit dans le Registre uniquement si aucune entrée n’existe.  
  
 *rglpszOverwrite*  
 Une liste d’entrées qui est écrit dans le Registre existent ou non toutes les entrées précédentes.  
  
 *bRegister*  
 Détermine si la classe doit être enregistré. Si *bRegister* a la valeur TRUE, la classe est inscrit auprès du Registre système. Sinon, il annule l’inscription de la classe.  
  
### <a name="remarks"></a>Notes  
 Les informations d’inscription sont chargées au moyen d’un appel à [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Les sous-chaînes extraites sont ceux identifiés par les index `regFileTypeId`, `regFileTypeName`, et `fileNewName`, comme décrit dans le `GetDocString` pages de référence.  
  
 Si le `regFileTypeId` sous-chaîne est vide ou si l’appel à `GetDocString` échoue pour toute autre raison, cette fonction échoue et les informations de fichier ne sont pas entrées dans le Registre.  
  
 Les informations contenues dans les arguments *rglpszRegister* et *rglpszOverwrite* est écrit dans le Registre via un appel à [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Les informations par défaut, qui sont enregistrées lorsque les deux arguments sont NULL, sont adaptées à la plupart des applications. Pour plus d’informations sur la structure des informations de ces arguments, consultez `AfxOleRegisterServerClass`.  
  
 Pour plus d’informations, consultez [Implementing the IDispatch Interface](http://msdn.microsoft.com/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC HIERSVR](../../visual-cpp-samples.md)   
 [COleObjectFactory (classe)](../../mfc/reference/coleobjectfactory-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)   
 [COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)
