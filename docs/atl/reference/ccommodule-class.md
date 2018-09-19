---
title: CComModule, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
dev_langs:
- C++
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: faf3080c6363ef0227b71e550ff658b1790d37b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090696"
---
# <a name="ccommodule-class"></a>CComModule (classe)

À compter d’ATL 7.0, `CComModule` est déconseillée : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComModule::GetClassObject](#getclassobject)|Crée un objet d’un CLSID spécifié. Pour les DLL.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Retourne `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Retourne `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Retourne `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Initialise les membres de données.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Passe à l’inscription de classe standard d’un objet dans le Registre système.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Enregistre l’objet de classe. Pour les exe.|
|[CComModule::RegisterServer](#registerserver)|Met à jour le Registre système pour chaque objet du mappage d’objets.|
|[CComModule::RegisterTypeLib](#registertypelib)|Inscrit une bibliothèque de types.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Révoque l’objet de classe. Pour les exe.|
|[CComModule::Term](#term)|Libère les membres de données.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Supprime l’inscription de classe standard d’un objet à partir du Registre système.|
|[CComModule::UnregisterServer](#unregisterserver)|Annule l’inscription de chaque objet du mappage d’objets.|
|[CComModule::UpdateRegistryClass](#updateregistryclass)|Inscrit ou annule l’inscription de l’inscription de classe standard d’un objet.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou désinscrire un objet.|
|[CComModule::UpdateRegistryFromResourceS](#updateregistryfromresources)|Liens statiquement au composant de Registre ATL. Exécute le script contenu dans une ressource spécifiée pour inscrire ou désinscrire un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Garantit un accès synchronisé à l’objet carte d’informations.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Garantit un accès synchronisé aux informations de bibliothèque de type.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Garantit un accès synchronisé aux informations de classe de fenêtre et les données statiques utilisées lors de la création de fenêtre.|
|[CComModule::m_hInst](#m_hinst)|Contient le handle de l’instance de module.|
|[CComModule::m_hInstResource](#m_hinstresource)|Par défaut, contient le handle vers l’instance de module.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Par défaut, contient le handle vers l’instance de module.|
|[CComModule::m_pObjMap](#m_pobjmap)|Pointe vers la table des objets gérés par l’instance de module.|

## <a name="remarks"></a>Notes

> [!NOTE]
>  Cette classe est déconseillée et les Assistants de génération de code ATL est maintenant utilisent le [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) et [CAtlModule](../../atl/reference/catlmodule-class.md) classes dérivées. Consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations. Les informations ci-dessous sont destiné aux applications créées avec des versions plus anciennes d’ATL. `CComModule` fait encore partie d’ATL pour descendante fonctionnalité.

`CComModule` implémente un module de serveur COM, ce qui permet un client d’accéder aux composants du module. `CComModule` prend en charge les DLL (-process) et les modules EXE (locales).

Un `CComModule` instance utilise un mappage de l’objet pour conserver un ensemble de définitions d’objet de classe. Ce mappage de l’objet est implémenté comme un tableau de `_ATL_OBJMAP_ENTRY` structures et contient des informations pour :

- Entrant et la suppression des descriptions des objets dans le Registre système.

- Lors de l’instanciation d’objets via une fabrique de classe.

- Établissement de la communication entre un client et l’objet racine dans le composant.

- Exécution de gestion de la durée de vie des objets de classe.

Lorsque vous exécutez l’ATL COM AppWizard, l’Assistant génère automatiquement `_Module`, une instance globale de `CComModule` ou une classe dérivée à partir de celui-ci. Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

En plus de `CComModule`, ATL fournit [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), qui implémente un module de modèle de cloisonnement pour les services de fichiers exe et Windows. Dériver votre module à partir de `CComAutoThreadModule` lorsque vous souhaitez créer des objets dans des cloisonnements plusieurs.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="getclassobject"></a>  CComModule::GetClassObject

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT GetClassObject(  
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
[in] Le CLSID de l’objet doit être créé.

*riid*<br/>
[in] IID de l’interface demandée.

*PPV*<br/>
[out] Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

`GetClassObject` est uniquement disponible pour les DLL.

##  <a name="getmoduleinstance"></a>  CComModule::GetModuleInstance

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

HINSTANCE identifiant ce module.

### <a name="remarks"></a>Notes

Retourne le [m_hInst](#m_hinst) membre de données.

##  <a name="getresourceinstance"></a>  CComModule::GetResourceInstance

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

HINSTANCE.

### <a name="remarks"></a>Notes

Retourne le [m_hInstResource](#m_hinstresource) membre de données.

##  <a name="gettypelibinstance"></a>  CComModule::GetTypeLibInstance

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Valeur de retour

HINSTANCE.

### <a name="remarks"></a>Notes

Retourne le [m_hInstTypeLib](#m_hinsttypelib) membre de données.

##  <a name="init"></a>  CComModule::Init

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Pointeur vers un tableau d’entrées de mappage d’objet.

*h*<br/>
[in] HINSTANCE passé à `DLLMain` ou `WinMain`.

*plibid*<br/>
[in] Pointeur vers le LIBID de la bibliothèque de types associé au projet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Initialise tous les membres de données.

##  <a name="m_csobjmap"></a>  CComModule::m_csObjMap

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Notes

Garantit un accès synchronisé au mappage d’objets.

##  <a name="m_cstypeinfoholder"></a>  CComModule::m_csTypeInfoHolder

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Notes

Garantit un accès synchronisé à la bibliothèque de types.

##  <a name="m_cswindowcreate"></a>  CComModule::m_csWindowCreate

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Notes

Garantit un accès synchronisé aux informations de classe de fenêtre et aux données statiques utilisées lors de la création de fenêtre.

##  <a name="m_hinst"></a>  CComModule::m_hInst

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Notes

Contient le handle de l’instance de module.

Le [Init](#init) méthode jeux `m_hInst` pour le handle passé à `DLLMain` ou `WinMain`.

##  <a name="m_hinstresource"></a>  CComModule::m_hInstResource

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Notes

Par défaut, contient le handle vers l’instance de module.

Le [Init](#init) méthode jeux `m_hInstResource` pour le handle passé à `DLLMain` ou `WinMain`. Vous pouvez définir explicitement `m_hInstResource` le handle vers une ressource.

Le [GetResourceInstance](#getresourceinstance) méthode retourne le handle stocké dans `m_hInstResource`.

##  <a name="m_hinsttypelib"></a>  CComModule::m_hInstTypeLib

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Notes

Par défaut, contient le handle vers l’instance de module.

Le [Init](#init) méthode jeux `m_hInstTypeLib` pour le handle passé à `DLLMain` ou `WinMain`. Vous pouvez définir explicitement `m_hInstTypeLib` le handle vers une bibliothèque de types.

Le [GetTypeLibInstance](#gettypelibinstance) méthode retourne le handle stocké dans `m_hInstTypeLib`.

##  <a name="m_pobjmap"></a>  CComModule::m_pObjMap

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Notes

Pointe vers la table des objets gérés par l’instance de module.

##  <a name="registerclasshelper"></a>  CComModule::RegisterClassHelper

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
ATL_DEPRECATED HRESULT RegisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le CLSID de l’objet à inscrire.

*lpszProgID*<br/>
[in] Le ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
[in] Le ProgID indépendants de la version associé à l’objet.

*nDescID*<br/>
[in] L’identificateur d’une ressource de chaîne de description de l’objet.

*dwFlags*<br/>
[in] Spécifie le modèle de thread à entrer dans le Registre. Les valeurs possibles sont THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Passe à l’inscription de classe standard d’un objet dans le Registre système.

Le [UpdateRegistryClass](#updateregistryclass) les appels de méthode `RegisterClassHelper`.

##  <a name="registerclassobjects"></a>  CComModule::RegisterClassObjects

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Paramètres

*dwClsContext*<br/>
[in] Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER. Pour obtenir une description de ces valeurs, consultez [CLSCTX](https://msdn.microsoft.com/library/windows/desktop/ms693716) dans le SDK Windows.

*dwFlags*<br/>
[in] Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE. Pour obtenir une description de ces valeurs, consultez [REGCLS](/windows/desktop/api/combaseapi/ne-combaseapi-tagregcls) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Inscrit un objet de classe EXE avec OLE pour d’autres applications peuvent se connecter à celui-ci. Cette méthode est uniquement disponible pour les exe.

##  <a name="registerserver"></a>  CComModule::RegisterServer

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,  
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
[in] Indique si la bibliothèque de types doit être inscrite. La valeur par défaut est FALSE.

*pCLSID*<br/>
[in] Pointe vers le CLSID de l’objet à inscrire. Si NULL (la valeur par défaut), tous les objets du mappage d’objets sera inscrit.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Selon le *pCLSID* paramètre, met à jour le Registre système pour un objet de classe unique ou pour tous les objets du mappage d’objets.

Si *bRegTypeLib* a la valeur TRUE, les informations de bibliothèque de type met également à jour.

Consultez [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour plus d’informations sur l’ajout d’une entrée au mappage d’objets.

`RegisterServer` sera appelée automatiquement par `DLLRegisterServer` pour une DLL ou par `WinMain` pour un EXE exécuter avec la `/RegServer` option de ligne de commande.

##  <a name="registertypelib"></a>  CComModule::RegisterTypeLib

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
[in] Chaîne au format `"\\N"`, où `N` est l’index d’entier de la ressource TYPELIB.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Ajoute des informations sur une bibliothèque de types dans le Registre système.

Si l’instance de module contient plusieurs bibliothèques de types, utilisez la deuxième version de cette méthode pour spécifier la bibliothèque de type doit être utilisée.

##  <a name="revokeclassobjects"></a>  CComModule::RevokeClassObjects

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Supprime l’objet de classe. Cette méthode est uniquement disponible pour les exe.

##  <a name="term"></a>  CComModule::Term

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
void Term() throw();
```

### <a name="remarks"></a>Notes

Libère tous les membres de données.

##  <a name="unregisterclasshelper"></a>  CComModule::UnregisterClassHelper

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[in] Le CLSID de l’objet doit être annulée.

*lpszProgID*<br/>
[in] Le ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
[in] Le ProgID indépendants de la version associé à l’objet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Supprime l’inscription de classe standard d’un objet à partir du Registre système.

Le [UpdateRegistryClass](#updateregistryclass) les appels de méthode `UnregisterClassHelper`.

##  <a name="unregisterserver"></a>  CComModule::UnregisterServer

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
Si la valeur est TRUE, la bibliothèque de types est également désinscrire.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet doit être annulée. Si la valeur NULL (la valeur par défaut), tous les objets du mappage d’objets sera annulée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Selon le *pCLSID* paramètre, annule l’inscription d’un objet de classe unique ou tous les objets du mappage d’objets.

`UnregisterServer` sera appelée automatiquement par `DLLUnregisterServer` pour une DLL ou par `WinMain` pour un EXE exécuter avec la `/UnregServer` option de ligne de commande.

Consultez [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour plus d’informations sur l’ajout d’une entrée au mappage d’objets.

##  <a name="updateregistryclass"></a>  CComModule::UpdateRegistryClass

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(  
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
Le CLSID de l’objet à être enregistré ou non.

*lpszProgID*<br/>
Le ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
Le ProgID indépendants de la version associé à l’objet.

*nDescID*<br/>
Identificateur de la ressource de chaîne de description de l’objet.

*szDesc*<br/>
Chaîne contenant la description de l’objet.

*dwFlags*<br/>
Spécifie le modèle de thread à entrer dans le Registre. Les valeurs possibles sont THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

*bRegister*<br/>
Indique si l’objet doit être inscrite.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si *bRegister* a la valeur TRUE, cette méthode passe à l’inscription de classe standard de l’objet dans le Registre système.

Si *bRegister* est FALSE, elle supprime l’inscription de l’objet.

Selon la valeur de *bRegister*, `UpdateRegistryClass` appelle [RegisterClassHelper](#registerclasshelper) ou [UnregisterClassHelper](#unregisterclasshelper).

En spécifiant le [DECLARE_REGISTRY](registry-macros.md#declare_registry) macro, `UpdateRegistryClass` sera appelé automatiquement lors du traitement de votre carte de l’objet.

##  <a name="updateregistryfromresourced"></a>  CComModule::UpdateRegistryFromResourceD

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
virtual HRESULT UpdateRegistryFromResourceD(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>Paramètres

*lpszRes*<br/>
[in] Un nom de ressource.

*nResID*<br/>
[in] Un ID de ressource.

*bRegister*<br/>
[in] Indique si l’objet doit être inscrite.

*pMapEntries*<br/>
[in] Pointeur vers la table de remplacement stocker des valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement `%MODULE%`. Pour utiliser les paramètres remplaçables supplémentaires, consultez la section Notes pour plus d’informations. Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Exécute le script contenu dans la ressource spécifiée par *lpszRes* ou *nResID*.

Si *bRegister* a la valeur TRUE, cette méthode inscrit l’objet dans le Registre système ; sinon, il annule l’inscription de l’objet.

En spécifiant le [macro DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro, `UpdateRegistryFromResourceD` sera appelé automatiquement lors du traitement de votre carte de l’objet.

> [!NOTE]
>  Pour remplacer les valeurs de remplacement en cours d’exécution, ne spécifiez pas la macro macro DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID. Au lieu de cela, créez un tableau de `_ATL_REGMAP_ENTRIES` structures, où chaque entrée contient un espace réservé variable associée à une valeur à remplacer l’espace réservé au moment de l’exécution. Appelez ensuite `UpdateRegistryFromResourceD`, en transmettant le tableau le *pMapEntries* paramètre. Cette opération ajoute toutes les valeurs de remplacement dans le `_ATL_REGMAP_ENTRIES` structures au mappage de remplacement du bureau d’enregistrement.

> [!NOTE]
>  Pour lier statiquement au composant de Registre ATL (inscription), consultez [UpdateRegistryFromResourceS](#updateregistryfromresources).

Pour plus d’informations sur les paramètres remplaçables et l’écriture de scripts, consultez l’article [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).

##  <a name="updateregistryfromresources"></a>  CComModule::UpdateRegistryFromResourceS

À compter d’ATL 7.0, `CComModule` est obsolète : consultez [Module ATL, Classes](../../atl/atl-module-classes.md) pour plus d’informations.

```
virtual HRESULT UpdateRegistryFromResourceS(  
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(  
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*lpszRes*<br/>
[in] Un nom de ressource.

*nResID*<br/>
[in] Un ID de ressource.

*bRegister*<br/>
[in] Indique si le script de ressources doit être inscrite.

*pMapEntries*<br/>
[in] Pointeur vers la table de remplacement stocker des valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement `%MODULE%`. Pour utiliser les paramètres remplaçables supplémentaires, consultez la section Notes pour plus d’informations. Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Semblable à [UpdateRegistryFromResourceD](#updateregistryfromresourced) sauf `UpdateRegistryFromResourceS` crée un lien statique vers le composant de Registre ATL (inscription).

`UpdateRegistryFromResourceS` sera appelé automatiquement lors du traitement de votre mappage d’objet fournie vous ajouter `#define _ATL_STATIC_REGISTRY` à votre fichier stdafx.h.

> [!NOTE]
>  Pour remplacer les valeurs de remplacement en cours d’exécution, ne spécifiez pas le [macro DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro. Au lieu de cela, créez un tableau de `_ATL_REGMAP_ENTRIES` structures, où chaque entrée contient un espace réservé variable associée à une valeur à remplacer l’espace réservé au moment de l’exécution. Appelez ensuite `UpdateRegistryFromResourceS`, en transmettant le tableau le *pMapEntries* paramètre. Cette opération ajoute toutes les valeurs de remplacement dans le `_ATL_REGMAP_ENTRIES` structures au mappage de remplacement du bureau d’enregistrement.

Pour plus d’informations sur les paramètres remplaçables et l’écriture de scripts, consultez l’article [le composant de Registre ATL (inscription)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
