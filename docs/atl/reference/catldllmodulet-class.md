---
title: Classe de CAtlDllModuleT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
dev_langs:
- C++
helpviewer_keywords:
- CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6b1ea8b5922454d32961f0e7d87eda16f55fe52c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364848"
---
# <a name="catldllmodulet-class"></a>Classe de CAtlDllModuleT
Cette classe représente le module d’une DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe dérivée de `CAtlDllModuleT`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|Constructeur.|  
|[CAtlDllModuleT :: ~ CAtlDllModuleT](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Teste si la DLL peut être déchargée.|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Retourne une fabrique de classe.|  
|[CAtlDllModuleT::DllMain](#dllmain)|Point d’entrée facultatif dans une bibliothèque de liens dynamiques (DLL).|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Ajoute des entrées au Registre du système pour les objets dans la DLL.|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Supprime les entrées dans le Registre système pour les objets dans la DLL.|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Retourne une fabrique de classe. Appelé par [DllGetClassObject](#dllgetclassobject).|  
  
## <a name="remarks"></a>Notes  
 `CAtlDllModuleT` représente le module pour une bibliothèque de liens dynamiques (DLL) et fournit des fonctions utilisées par tous les projets DLL. Cette spécialisation de [CAtlModuleT](../../atl/reference/catlmodulet-class.md) classe inclut la prise en charge pour l’inscription.  
  
 Pour plus d’informations sur les modules dans les ATL, consultez [Module ATL, Classes](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlbase.h  
  
##  <a name="catldllmodulet"></a>  CAtlDllModuleT::CAtlDllModuleT  
 Constructeur.  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>  CAtlDllModuleT :: ~ CAtlDllModuleT  
 Destructeur.  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>  CAtlDllModuleT::DllCanUnloadNow  
 Teste si la DLL peut être déchargée.  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 S’il ne peut pas, retourne S_OK si la DLL peut être déchargée ou S_FALSE.  
  
##  <a name="dllgetclassobject"></a>  CAtlDllModuleT::DllGetClassObject  
 Retourne la fabrique de classe.  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `rclsid`  
 Le CLSID de l’objet à créer.  
  
 `riid`  
 IID de l’interface demandée.  
  
 `ppv`  
 Un pointeur vers le pointeur d’interface identifié par `riid`. Si l’objet ne prend pas en charge cette interface, `ppv` a la valeur NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="dllmain"></a>  CAtlDllModuleT::DllMain  
 Point d’entrée facultatif dans une bibliothèque de liens dynamiques (DLL).  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `dwReason`  
 Si défini sur les appels de notification DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH et DLL_THREAD_DETACH est désactivé.  
  
 *lpReserved*  
 Réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours la valeur TRUE.  
  
### <a name="remarks"></a>Notes  
 La désactivation de la DLL_THREAD_ATTACH et DLL_THREAD_DETACH notification les appels peuvent être une optimisation utile pour les applications multithread qui ont de nombreuses DLL, qui fréquemment à créer et supprimer des threads, et dont les DLL n’avez pas besoin de ces notifications au niveau du thread de attachement/détachement.  
  
##  <a name="dllregisterserver"></a>  CAtlDllModuleT::DllRegisterServer  
 Ajoute des entrées au Registre du système pour les objets dans la DLL.  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `bRegTypeLib`  
 TRUE si la bibliothèque de types doit être enregistré. La valeur par défaut est TRUE.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="dllunregisterserver"></a>  CAtlDllModuleT::DllUnregisterServer  
 Supprime les entrées dans le Registre système pour les objets dans la DLL.  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `bUnRegTypeLib`  
 TRUE si la bibliothèque de types doit être supprimée du Registre. La valeur par défaut est TRUE.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
##  <a name="getclassobject"></a>  CAtlDllModuleT::GetClassObject  
 Crée un objet du CLSID spécifié.  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `rclsid`  
 Le CLSID de l’objet à créer.  
  
 `riid`  
 IID de l’interface demandée.  
  
 `ppv`  
 Un pointeur vers le pointeur d’interface identifié par `riid`. Si l’objet ne prend pas en charge cette interface, `ppv` a la valeur NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne S_OK en cas de réussite, ou une erreur HRESULT d’échec.  
  
### <a name="remarks"></a>Notes  
 Cette méthode est appelée par [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) et est inclus pour la compatibilité descendante.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
 [Classe de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [Module (Classes)](../../atl/atl-module-classes.md)
