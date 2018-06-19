---
title: Classe de CAtlComModule | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 47e85f3aab75f8fafb76977847ce36d37808af60
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364790"
---
# <a name="catlcommodule-class"></a>Classe de CAtlComModule
Cette classe implémente un module COM de serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|Constructeur.|  
|[CAtlComModule :: ~ CAtlComModule](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|Appelez cette méthode pour mettre à jour le Registre système pour chaque objet du mappage d’objets.|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Appelez cette méthode pour inscrire une bibliothèque de types.|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|Appelez cette méthode pour annuler l’inscription de chaque objet du mappage d’objets.|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Appelez cette méthode pour annuler l’inscription d’une bibliothèque de types.|  
  
## <a name="remarks"></a>Notes  
 `CAtlComModule` implémente un module de serveur COM, ce qui permet un client accéder aux composants du module.  
  
 Cette classe remplace l’obsolète [CComModule](../../atl/reference/ccommodule-class.md) classe utilisée dans les versions antérieures d’ATL. Consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule  
 Constructeur.  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le module.  
  
##  <a name="dtor"></a>  CAtlComModule :: ~ CAtlComModule  
 Destructeur.  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les fabriques de classe.  
  
##  <a name="registerserver"></a>  CAtlComModule::RegisterServer  
 Appelez cette méthode pour mettre à jour le Registre système pour chaque objet du mappage d’objets.  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `bRegTypeLib`  
 TRUE si la bibliothèque de types doit être enregistré. La valeur par défaut est FALSE.  
  
 `pCLSID`  
 Pointe vers le CLSID de l’objet à inscrire. Si NULL (la valeur par défaut), tous les objets du mappage d’objets sera inscrit.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Appelle la fonction globale [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).  
  
##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib  
 Appelez cette méthode pour inscrire une bibliothèque de types.  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszIndex`  
 Chaîne au format «\\\N », où N est l’index d’entiers de la ressource de bibliothèque de types.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Ajoute des informations sur une bibliothèque de types dans le Registre système. Si l’instance de module contient plusieurs bibliothèques de types, utilisez la première version de cette méthode pour spécifier le type de bibliothèque doit être utilisé.  
  
##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer  
 Appelez cette méthode pour annuler l’inscription de chaque objet du mappage d’objets.  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `bRegTypeLib`  
 TRUE si la bibliothèque de types doit être annulée. La valeur par défaut est FALSE.  
  
 `pCLSID`  
 Pointe vers le CLSID de l’objet doit être annulée. Si la valeur NULL (valeur par défaut), tous les objets du mappage d’objets sera annulée.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Appelle la fonction globale [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).  
  
##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib  
 Appelez cette méthode pour annuler l’inscription d’une bibliothèque de types.  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszIndex`  
 Chaîne au format «\\\N », où N est l’index d’entiers de la ressource de bibliothèque de types.  
  
### <a name="remarks"></a>Notes  
 Supprime les informations sur une bibliothèque de types à partir du Registre système. Si l’instance de module contient plusieurs bibliothèques de types, utilisez la première version de cette méthode pour spécifier le type de bibliothèque doit être utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
## <a name="see-also"></a>Voir aussi  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
