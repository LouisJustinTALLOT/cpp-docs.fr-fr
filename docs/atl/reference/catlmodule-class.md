---
title: Classe de CAtlModule | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlModule
- ATLBASE/ATL::CAtlModule
- ATLBASE/ATL::CAtlModule::CAtlModule
- ATLBASE/ATL::CAtlModule::AddCommonRGSReplacements
- ATLBASE/ATL::CAtlModule::AddTermFunc
- ATLBASE/ATL::CAtlModule::GetGITPtr
- ATLBASE/ATL::CAtlModule::GetLockCount
- ATLBASE/ATL::CAtlModule::Lock
- ATLBASE/ATL::CAtlModule::Term
- ATLBASE/ATL::CAtlModule::Unlock
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceDHelper
- ATLBASE/ATL::CAtlModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CAtlModule::m_libid
- ATLBASE/ATL::CAtlModule::m_pGIT
dev_langs:
- C++
helpviewer_keywords:
- CAtlModule class
ms.assetid: 63fe02f1-4c4b-4e7c-ae97-7ad7b4252415
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2be5d5a777d4b9aed9ee4d07016771ee91c913b0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365280"
---
# <a name="catlmodule-class"></a>Classe de CAtlModule
Cette classe fournit des méthodes utilisées par plusieurs classes du module ATL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class ATL_NO_VTABLE CAtlModule : public _ATL_MODULE
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlModule::CAtlModule](#catlmodule)|Constructeur.|  
|[CAtlModule :: ~ CAtlModule](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements)|Substituez cette méthode pour ajouter des paramètres à la table de remplacement de composant de Registre ATL (inscription).|  
|[CAtlModule::AddTermFunc](#addtermfunc)|Ajoute une nouvelle fonction à appeler lorsque le module se termine.|  
|[CAtlModule::GetGITPtr](#getgitptr)|Retourne le pointeur d’Interface globale.|  
|[CAtlModule::GetLockCount](#getlockcount)|Retourne le nombre de verrous.|  
|[CAtlModule::Lock](#lock)|Incrémente le nombre de verrous.|  
|[CAtlModule::Term](#term)|Libère tous les membres de données.|  
|[CAtlModule::Unlock](#unlock)|Décrémente le nombre de verrous.|  
|[CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet.|  
|[CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper)|Cette méthode est appelée par `UpdateRegistryFromResourceD` pour effectuer la mise à jour du Registre.|  
|[CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet. Cette méthode lie statiquement au composant de Registre ATL.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlModule::m_libid](#m_libid)|Contient le GUID du module actuel.|  
|[CAtlModule::m_pGIT](#m_pgit)|Pointeur vers le tableau Global d’Interface.|  
  
## <a name="remarks"></a>Notes  
 Cette classe est utilisée par [CAtlDllModuleT classe](../../atl/reference/catldllmodulet-class.md), [CAtlExeModuleT classe](../../atl/reference/catlexemodulet-class.md), et [CAtlServiceModuleT classe](../../atl/reference/catlservicemodulet-class.md) pour prendre en charge pour les applications de la DLL, les applications EXE, et Services Windows, respectivement.  
  
 Pour plus d’informations sur les modules dans les ATL, consultez [Module ATL, Classes](../../atl/atl-module-classes.md).  
  
 Cette classe remplace l’obsolète [CComModule (classe)](../../atl/reference/ccommodule-class.md) utilisé dans les versions antérieures d’ATL.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 `CAtlModule`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="addcommonrgsreplacements"></a>  CAtlModule::AddCommonRGSReplacements  
 Substituez cette méthode pour ajouter des paramètres à la table de remplacement de composant de Registre ATL (inscription).  
  
```
virtual HRESULT AddCommonRGSReplacements(IRegistrarBase* /* pRegistrar*/) throw() = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 *pRegistrar*  
 Réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Paramètres remplaçables autorisent le client du bureau d’enregistrement spécifier les données de l’exécution. Pour ce faire, Registrar maintient un mappage de remplacement dans laquelle il entre les valeurs associées aux paramètres remplaçables dans votre script. Le bureau d’enregistrement effectue ces entrées au moment de l’exécution.  
  
 Consultez la rubrique [à l’aide des paramètres remplaçables (le préprocesseur de Registrar)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) pour plus d’informations.  
  
##  <a name="addtermfunc"></a>  CAtlModule::AddTermFunc  
 Ajoute une nouvelle fonction à appeler lorsque le module se termine.  
  
```
HRESULT AddTermFunc(_ATL_TERMFUNC* pFunc, DWORD_PTR dw) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pFunc*  
 Pointeur vers la fonction à ajouter.  
  
 `dw`  
 Données définies par l’utilisateur, passé à la fonction.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="catlmodule"></a>  CAtlModule::CAtlModule  
 Constructeur.  
  
```
CAtlModule() throw();
```  
  
### <a name="remarks"></a>Notes  
 Initialise les membres de données et lance une section critique autour de thread du module.  
  
##  <a name="dtor"></a>  CAtlModule :: ~ CAtlModule  
 Destructeur.  
  
```
~CAtlModule() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère tous les membres de données.  
  
##  <a name="getgitptr"></a>  CAtlModule::GetGITPtr  
 Récupère un pointeur vers la Table d’Interface globale.  
  
```
virtual HRESULT GetGITPtr(IGlobalInterfaceTable** ppGIT) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `ppGIT`  
 Pointeur vers la variable qui reçoit le pointeur vers la Table d’Interface globale.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite ou un code d’erreur en cas d’échec. E_POINTER est retournée si `ppGIT` est égal à NULL.  
  
### <a name="remarks"></a>Notes  
 Si l’objet Global Interface Table n’existe pas, il est créé et son adresse est stockée dans la variable membre [CAtlModule::m_pGIT](#m_pgit).  
  
 Dans les versions debug, une erreur d’assertion se produit si `ppGIT` est égal à NULL, ou si le pointeur de la Table d’Interface globale ne peut pas être obtenu.  
  
 Consultez [IGlobalInterfaceTable](http://msdn.microsoft.com/library/windows/desktop/ms678517) pour plus d’informations sur la Table d’Interface globale.  
  
##  <a name="getlockcount"></a>  CAtlModule::GetLockCount  
 Retourne le nombre de verrous.  
  
```
virtual LONG GetLockCount() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de verrous. Cette valeur peut être utile pour les tests de diagnostic et de débogage.  
  
##  <a name="lock"></a>  CAtlModule::Lock  
 Incrémente le nombre de verrous.  
  
```
virtual LONG Lock() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Incrémente le nombre de verrous et retourne la valeur mise à jour. Cette valeur peut être utile pour les tests de diagnostic et de débogage.  
  
##  <a name="m_libid"></a>  CAtlModule::m_libid  
 Contient le GUID du module actuel.  
  
```
static GUID m_libid;
```  
  
##  <a name="m_pgit"></a>  CAtlModule::m_pGIT  
 Pointeur vers le tableau Global d’Interface.  
  
```
IGlobalInterfaceTable* m_pGIT;
```  
  
##  <a name="term"></a>  CAtlModule::Term  
 Libère tous les membres de données.  
  
```
void Term() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère tous les membres de données. Cette méthode est appelée par le destructeur.  
  
##  <a name="unlock"></a>  CAtlModule::Unlock  
 Décrémente le nombre de verrous.  
  
```
virtual LONG Unlock() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Décrémente le nombre de verrous et retourne la valeur mise à jour. Cette valeur peut être utile pour les tests de diagnostic et de débogage.  
  
##  <a name="updateregistryfromresourced"></a>  CAtlModule::UpdateRegistryFromResourceD  
 Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet.  
  
```
HRESULT WINAPI UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszRes`  
 Un nom de ressource.  
  
 `nResID`  
 Un ID de ressource.  
  
 `bRegister`  
 **TRUE** si l’objet doit être inscrit ; **FALSE** dans le cas contraire.  
  
 `pMapEntries`  
 Pointeur vers la table de remplacement le stockage des valeurs associées avec les paramètres remplaçables du script. ATL utilise automatiquement le MODULE %. Pour utiliser des paramètres remplaçables supplémentaires, consultez [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez le **NULL** valeur par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Exécute le script contenu dans la ressource spécifiée par *lpszRes ou nResID*. Si `bRegister` est **TRUE**, cette méthode enregistre l’objet dans le Registre système ; sinon, elle supprime l’objet à partir du Registre.  
  
 Pour lier statiquement au composant de Registre ATL (inscription), voir [CAtlModule::UpdateRegistryFromResourceS](#updateregistryfromresources).  
  
 Cette méthode appelle [CAtlModule::UpdateRegistryFromResourceDHelper](#updateregistryfromresourcedhelper) et [IRegistrar::ResourceUnregister](iregistrar-class.md#resourceunregister).  
  
##  <a name="updateregistryfromresourcedhelper"></a>  CAtlModule::UpdateRegistryFromResourceDHelper  
 Cette méthode est appelée par `UpdateRegistryFromResourceD` pour effectuer la mise à jour du Registre.  
  
```
inline HRESULT WINAPI UpdateRegistryFromResourceDHelper(  
    LPCOLESTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lpszRes`  
 Un nom de ressource.  
  
 `bRegister`  
 Indique si l’objet doit être inscrit.  
  
 `pMapEntries`  
 Pointeur vers la table de remplacement le stockage des valeurs associées avec les paramètres remplaçables du script. ATL utilise automatiquement le MODULE %. Pour utiliser des paramètres remplaçables supplémentaires, consultez [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez le **NULL** valeur par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode fournit l’implémentation de [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced).  
  
##  <a name="updateregistryfromresources"></a>  CAtlModule::UpdateRegistryFromResourceS  
 Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet. Cette méthode lie statiquement au composant de Registre ATL.  
  
```
HRESULT WINAPI UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

HRESULT WINAPI UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nResID`  
 Un ID de ressource.  
  
 `lpszRes`  
 Un nom de ressource.  
  
 `bRegister`  
 Indique si le script de ressources doit être enregistré.  
  
 `pMapEntries`  
 Pointeur vers la table de remplacement le stockage des valeurs associées avec les paramètres remplaçables du script. ATL utilise automatiquement le MODULE %. Pour utiliser des paramètres remplaçables supplémentaires, consultez [CAtlModule::AddCommonRGSReplacements](#addcommonrgsreplacements). Sinon, utilisez le **NULL** valeur par défaut.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Semblable à [CAtlModule::UpdateRegistryFromResourceD](#updateregistryfromresourced) sauf `CAtlModule::UpdateRegistryFromResourceS` crée un lien statique vers le composant de Registre ATL (inscription).  
  
## <a name="see-also"></a>Voir aussi  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Module (Classes)](../../atl/atl-module-classes.md)   
 [Composant de Registre (inscription)](../../atl/atl-registry-component-registrar.md)  
