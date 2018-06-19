---
title: Mappages de connexion | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.maps
dev_langs:
- C++
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 475314edba2a11535349991db644a4915e352ae7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372836"
---
# <a name="connection-maps"></a>Tables de connexions
Contrôles OLE sont en mesure d’exposer les interfaces à d’autres applications. Ces interfaces permettent uniquement l’accès à partir d’un conteneur dans ce contrôle. Si un contrôle OLE souhaite accéder à des interfaces externes d’autres objets OLE, un point de connexion doit être établi. Ce point de connexion permet à un contrôle sortant à des tables de dispatch externes, tels que les tables d’événements ou des fonctions de notification.  
  
 La bibliothèque Microsoft Foundation Class offre un modèle de programmation qui prend en charge les points de connexion. Dans ce modèle, « connexion mappe » sont utilisées pour désigner des interfaces ou des points de connexion pour le contrôle OLE. Mappages de connexion contiennent une macro pour chaque point de connexion. Pour plus d’informations sur les mappages de connexion, consultez le [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) classe.  
  
 En règle générale, un contrôle prend en charge deux points de connexion : un pour les événements et l’autre pour les notifications de la propriété. Celles-ci sont implémentées par le `COleControl` classe de base et ne nécessitent aucun travail supplémentaire par le writer de contrôle. Les points de connexion supplémentaires que vous souhaitez implémenter dans votre classe doivent être ajoutés manuellement. Pour prendre en charge les mappages de connexion et les points, MFC fournit les macros suivantes :  
  
### <a name="connection-map-declaration-and-demarcation"></a>Connexion déclaration et démarcation de table  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_PART](#begin_connection_part)|Déclare une classe incorporée qui implémente un point de connexion supplémentaires (doit être utilisé dans la déclaration de classe).|  
|[END_CONNECTION_PART](#end_connection_part)|Met fin à la déclaration d’un point de connexion (doit être utilisé dans la déclaration de classe).|  
|[CONNECTION_IID](#connection_iid)|Spécifie l’ID de l’interface du contrôle point de connexion.|  
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|Déclare qu’un mappage de connexion est utilisé dans une classe (doit être utilisé dans la déclaration de classe).|  
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|Commence la définition d’un mappage de connexions (doit être utilisé dans l’implémentation de classe).|  
|[END_CONNECTION_MAP](#end_connection_map)|Termine la définition d’un mappage de connexions (doit être utilisé dans l’implémentation de classe).|  
|[CONNECTION_PART](#connection_part)|Spécifie un point de connexion dans le mappage de connexions du contrôle.|  
  
 Les fonctions suivantes aider un récepteur dans l’établissement et la déconnexion d’une connexion à l’aide de points de connexion :  
  
### <a name="initializationtermination-of-connection-points"></a>Initialisation et d’arrêt des Points de connexion  
  
|||  
|-|-|  
|[AfxConnectionAdvise](#afxconnectionadvise)|Établit une connexion entre une source et un récepteur.|  
|[AfxConnectionUnadvise](#afxconnectionunadvise)|Arrête une connexion entre une source et un récepteur.|  
  
##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART  
 Utilisez le `BEGIN_CONNECTION_PART` macro pour commencer la définition de points de connexion supplémentaires au-delà de points de connexion de notifications événement et une propriété.  
  
```   
BEGIN_CONNECTION_PART(theClass, localClass)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Spécifie le nom de la classe de contrôle dont la connexion pointe ainsi.  
  
 *localClass*  
 Spécifie le nom de la classe locale qui implémente le point de connexion.  
  
### <a name="remarks"></a>Notes  
 Dans le fichier de déclaration (.h) qui définit les fonctions membres pour votre classe, démarrer le point de connexion avec le `BEGIN_CONNECTION_PART` (macro), puis ajoutez le `CONNECTION_IID` (macro) et autres fonctions de membre que vous souhaitez implémenter et effectuer le mappage de point de connexion avec la `END_CONNECTION_PART` (macro).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="end_connection_part"></a>  END_CONNECTION_PART  
 Met fin à la déclaration de votre point de connexion.  
  
```   
END_CONNECTION_PART(localClass)   
```  
  
### <a name="parameters"></a>Paramètres  
 *localClass*  
 Spécifie le nom de la classe locale qui implémente le point de connexion.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="connection_iid"></a>  CONNECTION_IID  
 Utilisez entre le `BEGIN_CONNECTION_PART` et `END_CONNECTION_PART` macros pour définir un ID d’interface pour un point de connexion pris en charge par votre contrôle OLE.  
  
```   
CONNECTION_IID(iid)   
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 L’ID de l’interface appelée par le point de connexion.  
  
### <a name="remarks"></a>Notes  
 Le `iid` argument est un ID d’interface utilisé pour identifier l’interface qui appelle le point de connexion sur son récepteurs connectés. Par exemple :  
  
 [!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]  
  
 Spécifie un point de connexion qui appelle le `ISinkInterface` interface.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP  
 Chaque `COleControl`-classe dérivée dans votre programme peut fournir un mappage de connexion pour spécifier des points de connexion supplémentaires qui prend en charge de votre contrôle.  
  
```   
DECLARE_CONNECTION_MAP() 
```  
  
### <a name="remarks"></a>Notes  
 Si votre contrôle prend en charge des points supplémentaires, utilisez le `DECLARE_CONNECTION_MAP` (macro) à la fin de votre déclaration de classe. Puis, dans le fichier .cpp qui définit les fonctions membres de la classe, utilisez le `BEGIN_CONNECTION_MAP` macro, `CONNECTION_PART` macros pour chacun des points de connexion du contrôle et le `END_CONNECTION_MAP` macro pour déclarer la fin de la table de connexion.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP  
 Chaque `COleControl`-classe dérivée dans votre programme peut fournir un mappage de connexion pour spécifier des points de connexion qui prend en charge votre contrôle.  
  
```   
BEGIN_CONNECTION_MAP(theClass, theBase)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Spécifie le nom de la classe de contrôle dont la connexion mapper.  
  
 *theBase*  
 Spécifie le nom de la classe de base `theClass`.  
  
### <a name="remarks"></a>Notes  
 Dans l’implémentation (. Fichier CPP) qui définit les fonctions membres de votre classe, démarrer le mappage de connexion avec le `BEGIN_CONNECTION_MAP` (macro), puis ajoutez les entrées de la macro pour chacun de vos points de connexion à l’aide de la [CONNECTION_PART](#connection_part) (macro). Pour finir, terminez le mappage de connexion avec le [END_CONNECTION_MAP](#end_connection_map) (macro).  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="end_connection_map"></a>  END_CONNECTION_MAP  
 Met fin à la définition de votre mappage de connexion.  
  
```   
END_CONNECTION_MAP()  
```  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="connection_part"></a>  CONNECTION_PART  
 Mappe un point de connexion pour votre contrôle OLE à un ID d’interface spécifique.  
  
```   
CONNECTION_PART(theClass, iid, localClass)   
```  
  
### <a name="parameters"></a>Paramètres  
 `theClass`  
 Spécifie le nom de la classe de contrôle dont la connexion pointe ainsi.  
  
 `iid`  
 L’ID de l’interface appelée par le point de connexion.  
  
 *localClass*  
 Spécifie le nom de la classe locale qui implémente le point de connexion.  
  
### <a name="remarks"></a>Notes  
 Par exemple :  
  
 [!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]  
  
 implémente un mappage de connexion, avec un point de connexion, qui appelle la `IID_ISinkInterface` interface.  
  
### <a name="requirements"></a>Spécifications  
  **En-tête** afxdisp.h  
  
##  <a name="afxconnectionadvise"></a>  AfxConnectionAdvise  
 Appelez cette fonction pour établir une connexion entre une source spécifiée par `pUnkSrc`et un récepteur spécifié par `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD FAR* pdwCookie);
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkSrc`  
 Pointeur vers l’objet qui appelle l’interface.  
  
 `pUnkSink`  
 Pointeur vers l’objet qui implémente l’interface.  
  
 `iid`  
 L’ID de la connexion.  
  
 `bRefCount`  
 **TRUE** indique que la création de la connexion doit entraîner le décompte de références de `pUnkSink` à incrémenter. **FALSE** indique que le nombre de référence ne doit pas être incrémenté.  
  
 `pdwCookie`  
 Un pointeur vers un `DWORD` où un identificateur de connexion est retourné. Cette valeur doit être passée en tant que le `dwCookie` paramètre `AfxConnectionUnadvise` lors de la déconnexion de la connexion.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une connexion a été établie ; Sinon, 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h 

##  <a name="afxconnectionunadvise"></a>  AfxConnectionUnadvise  
 Appelez cette fonction pour déconnecter une connexion entre une source spécifiée par `pUnkSrc`et un récepteur spécifié par `pUnkSink`.  
  
```   
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc, 
    REFIID iid, 
    LPUNKNOWN pUnkSink, 
    BOOL bRefCount, 
    DWORD dwCookie); 
```  
  
### <a name="parameters"></a>Paramètres  
 `pUnkSrc`  
 Pointeur vers l’objet qui appelle l’interface.  
  
 `pUnkSink`  
 Pointeur vers l’objet qui implémente l’interface.  
  
 `iid`  
 L’ID d’interface de l’interface de point de connexion.  
  
 `bRefCount`  
 **TRUE** indique que la déconnexion de la connexion doit entraîner le décompte de références de `pUnkSink` à décrémenter. **FALSE** indique que le nombre de référence ne doit pas être décrémenté.  
  
 `dwCookie`  
 L’identificateur de connexion renvoyé par `AfxConnectionAdvise`.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si une connexion a été interrompue ; Sinon, 0.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxctl.h 

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
