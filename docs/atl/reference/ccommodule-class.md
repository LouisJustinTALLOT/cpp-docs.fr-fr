---
description: 'En savoir plus sur : CComModule, classe'
title: CComModule (classe)
ms.date: 08/19/2019
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
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: dd0ec6c6aa7d68374a90830b10815a9cbdd54aeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152020"
---
# <a name="ccommodule-class"></a>CComModule (classe)

À partir de ATL 7,0, `CComModule` est déconseillé : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComModule :: GetClassObject,](#getclassobject)|Crée un objet d’un CLSID spécifié. Pour les dll uniquement.|
|[CComModule :: GetModuleInstance](#getmoduleinstance)|Retourne `m_hInst`.|
|[CComModule :: GetResourceInstance](#getresourceinstance)|Retourne `m_hInstResource`.|
|[CComModule :: GetTypeLibInstance](#gettypelibinstance)|Retourne `m_hInstTypeLib`.|
|[CComModule :: init](#init)|Initialise des membres de données.|
|[CComModule :: RegisterClassHelper](#registerclasshelper)|Entre l’inscription de la classe standard d’un objet dans le registre système.|
|[CComModule :: RegisterClassObjects](#registerclassobjects)|Inscrit l’objet de classe. Pour les fichiers exe uniquement.|
|[CComModule :: RegisterServer](#registerserver)|Met à jour le registre système pour chaque objet du mappage d’objets.|
|[CComModule :: RegisterTypeLib](#registertypelib)|Inscrit une bibliothèque de types.|
|[CComModule :: RevokeClassObjects](#revokeclassobjects)|Révoque l’objet de classe. Pour les fichiers exe uniquement.|
|[CComModule :: term](#term)|Libère des membres de données.|
|[CComModule :: UnregisterClassHelper](#unregisterclasshelper)|Supprime l’inscription de classe standard d’un objet du Registre système.|
|[CComModule :: UnregisterServer](#unregisterserver)|Annule l’inscription de chaque objet dans la table des objets.|
|[CComModule :: UpdateRegistryClass](#updateregistryclass)|Inscrit ou annule l’inscription de l’inscription de classe standard d’un objet.|
|[CComModule :: UpdateRegistryFromResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet.|
|[CComModule :: UpdateRegistryFromResourceS](#updateregistryfromresources)|Liens statiques vers le composant de Registre ATL. Exécute le script contenu dans une ressource spécifiée pour inscrire ou annuler l’inscription d’un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComModule :: m_csObjMap](#m_csobjmap)|Garantit un accès synchronisé aux informations de mappage d’objets.|
|[CComModule :: m_csTypeInfoHolder](#m_cstypeinfoholder)|Garantit un accès synchronisé aux informations de la bibliothèque de types.|
|[CComModule :: m_csWindowCreate](#m_cswindowcreate)|Garantit un accès synchronisé aux informations de classe de fenêtre et aux données statiques utilisées pendant la création de la fenêtre.|
|[CComModule :: m_hInst](#m_hinst)|Contient le handle de l’instance de module.|
|[CComModule :: m_hInstResource](#m_hinstresource)|Par défaut, contient le handle de l’instance de module.|
|[CComModule :: m_hInstTypeLib](#m_hinsttypelib)|Par défaut, contient le handle de l’instance de module.|
|[CComModule :: m_pObjMap](#m_pobjmap)|Pointe vers le mappage d’objet géré par l’instance de module.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette classe est déconseillée et les assistants de génération de code ATL utilisent désormais les classes dérivées [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) et [CAtlModule](../../atl/reference/catlmodule-class.md) . Pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) . Les informations suivantes sont destinées à être utilisées avec les applications créées avec des versions antérieures d’ATL. `CComModule` fait toujours partie de ATL pour la fonctionnalité descendante.

`CComModule` implémente un module serveur COM, permettant à un client d’accéder aux composants du module. `CComModule` prend en charge les modules DLL (in-process) et EXE (local).

Une `CComModule` instance utilise un mappage d’objet pour conserver un ensemble de définitions d’objets de classe. Ce mappage d’objets est implémenté en tant que tableau de `_ATL_OBJMAP_ENTRY` structures et contient des informations pour :

- Entrée et suppression des descriptions d’objets dans le registre système.

- Instanciation d’objets par le biais d’une fabrique de classe.

- Établissement de la communication entre un client et l’objet racine dans le composant.

- Réalisation de la gestion de la durée de vie des objets de classe.

Quand vous exécutez ATL COM AppWizard, l’Assistant génère automatiquement `_Module` , une instance globale de `CComModule` ou une classe dérivée de celui-ci. Pour plus d’informations sur l’Assistant Projet ATL, consultez l’article [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

En plus de `CComModule` , ATL fournit [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), qui implémente un module de modèle cloisonné pour les fichiers exe et les services Windows. Dérivez votre module de `CComAutoThreadModule` lorsque vous souhaitez créer des objets dans plusieurs cloisons.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a> CComModule :: GetClassObject,

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
dans CLSID de l’objet à créer.

*riid*<br/>
dans IID de l’interface demandée.

*ppv*<br/>
à Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *PPV* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

`GetClassObject` est uniquement disponible pour les dll.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a> CComModule :: GetModuleInstance

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valeur renvoyée

HINSTANCE identifiant ce module.

### <a name="remarks"></a>Notes

Retourne le membre de données [m_hInst](#m_hinst) .

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a> CComModule :: GetResourceInstance

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valeur renvoyée

HINSTANCE.

### <a name="remarks"></a>Notes

Retourne le membre de données [m_hInstResource](#m_hinstresource) .

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a> CComModule :: GetTypeLibInstance

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

HINSTANCE.

### <a name="remarks"></a>Notes

Retourne le membre de données [m_hInstTypeLib](#m_hinsttypelib) .

## <a name="ccommoduleinit"></a><a name="init"></a> CComModule :: init

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers un tableau d’entrées de mappage d’objets.

*h*<br/>
dans HINSTANCE passé à `DLLMain` ou `WinMain` .

*plibid*<br/>
dans Pointeur vers le LIBID de la bibliothèque de types associée au projet.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Initialise tous les membres de données.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a> CComModule :: m_csObjMap

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Notes

Garantit l’accès synchronisé à la table d’objets.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a> CComModule :: m_csTypeInfoHolder

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Notes

Garantit un accès synchronisé à la bibliothèque de types.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a> CComModule :: m_csWindowCreate

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Notes

Garantit un accès synchronisé aux informations de classe de fenêtre et aux données statiques utilisées pendant la création de la fenêtre.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a> CComModule :: m_hInst

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Notes

Contient le handle de l’instance de module.

La méthode [init](#init) définit `m_hInst` sur le handle passé à `DLLMain` ou `WinMain` .

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a> CComModule :: m_hInstResource

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Notes

Par défaut, contient le handle de l’instance de module.

La méthode [init](#init) définit `m_hInstResource` sur le handle passé à `DLLMain` ou `WinMain` . Vous pouvez définir explicitement `m_hInstResource` sur le handle d’une ressource.

La méthode [GetResourceInstance](#getresourceinstance) retourne le descripteur stocké dans `m_hInstResource` .

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a> CComModule :: m_hInstTypeLib

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Notes

Par défaut, contient le handle de l’instance de module.

La méthode [init](#init) définit `m_hInstTypeLib` sur le handle passé à `DLLMain` ou `WinMain` . Vous pouvez définir explicitement `m_hInstTypeLib` sur le handle d’une bibliothèque de types.

La méthode [GetTypeLibInstance](#gettypelibinstance) retourne le descripteur stocké dans `m_hInstTypeLib` .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a> CComModule :: m_pObjMap

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Notes

Pointe vers le mappage d’objet géré par l’instance de module.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a> CComModule :: RegisterClassHelper

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
dans CLSID de l’objet à inscrire.

*lpszProgID*<br/>
dans ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
dans ProgID indépendant de la version associé à l’objet.

*nDescID*<br/>
dans Identificateur d’une ressource de type chaîne pour la description de l’objet.

*dwFlags*<br/>
dans Spécifie le modèle de thread à entrer dans le registre. Les valeurs possibles sont THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Entre l’inscription de la classe standard d’un objet dans le registre système.

La méthode [UpdateRegistryClass](#updateregistryclass) appelle `RegisterClassHelper` .

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a> CComModule :: RegisterClassObjects

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Paramètres

*dwClsContext*<br/>
dans Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER. Pour obtenir une description de ces valeurs, consultez [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) dans le SDK Windows.

*dwFlags*<br/>
dans Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE. Pour obtenir une description de ces valeurs, consultez [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) dans le SDK Windows.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Inscrit un objet de classe EXE avec OLE pour permettre à d’autres applications de s’y connecter. Cette méthode est uniquement disponible pour les fichiers exe.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a> CComModule :: RegisterServer

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
dans Indique si la bibliothèque de types est inscrite. La valeur par défaut est FALSE.

*pCLSID*<br/>
dans Pointe vers le CLSID de l’objet à inscrire. Si la valeur est NULL (valeur par défaut), tous les objets dans le mappage d’objets sont inscrits.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

En fonction du paramètre *pCLSID* , met à jour le registre système pour un objet de classe unique ou pour tous les objets dans le mappage d’objets.

Si *bRegTypeLib* a la valeur true, les informations de la bibliothèque de types sont également mises à jour.

Pour plus d’informations sur l’ajout d’une entrée à la table d’objets, consultez [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

`RegisterServer` est appelé automatiquement par `DLLRegisterServer` pour une dll ou par `WinMain` pour une exécution exe avec l' `/RegServer` option de ligne de commande.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a> CComModule :: RegisterTypeLib

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
dans Chaîne au format `"\\N"` , où `N` est l’index d’entiers de la ressource TypeLib.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Ajoute des informations sur une bibliothèque de types au registre système.

Si l’instance de module contient plusieurs bibliothèques de types, utilisez la deuxième version de cette méthode pour spécifier la bibliothèque de types à utiliser.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a> CComModule :: RevokeClassObjects

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Supprime l’objet de classe. Cette méthode est uniquement disponible pour les fichiers exe.

## <a name="ccommoduleterm"></a><a name="term"></a> CComModule :: term

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```cpp
void Term() throw();
```

### <a name="remarks"></a>Notes

Libère tous les membres de données.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a> CComModule :: UnregisterClassHelper

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
dans CLSID de l’objet dont l’inscription doit être annulée.

*lpszProgID*<br/>
dans ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
dans ProgID indépendant de la version associé à l’objet.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Supprime l’inscription de classe standard d’un objet du Registre système.

La méthode [UpdateRegistryClass](#updateregistryclass) appelle `UnregisterClassHelper` .

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a> CComModule :: UnregisterServer

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
Si la valeur est TRUE, l’inscription de la bibliothèque de types est également annulée.

*pCLSID*<br/>
Pointe vers le CLSID de l’objet dont l’inscription doit être annulée. Si la valeur est NULL (valeur par défaut), tous les objets dans le mappage d’objets sont désinscrits.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Selon le paramètre *pCLSID* , annule l’inscription d’un objet de classe unique ou de tous les objets de la table d’objets.

`UnregisterServer` est appelé automatiquement par `DLLUnregisterServer` pour une dll ou par `WinMain` pour une exécution exe avec l' `/UnregServer` option de ligne de commande.

Pour plus d’informations sur l’ajout d’une entrée à la table d’objets, consultez [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a> CComModule :: UpdateRegistryClass

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

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

*identificateur*<br/>
CLSID de l’objet à inscrire ou désinscrit.

*lpszProgID*<br/>
ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
ProgID indépendant de la version associé à l’objet.

*nDescID*<br/>
Identificateur de la ressource de type chaîne pour la description de l’objet.

*szDesc*<br/>
Chaîne contenant la description de l’objet.

*dwFlags*<br/>
Spécifie le modèle de thread à entrer dans le registre. Les valeurs possibles sont THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

*bRegister*<br/>
Indique si l’objet doit être enregistré.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si *bRegister* a la valeur true, cette méthode accède à l’inscription de la classe standard de l’objet dans le registre système.

Si *bRegister* a la valeur false, l’inscription de l’objet est supprimée.

Selon la valeur de *bRegister*, `UpdateRegistryClass` appelle [RegisterClassHelper](#registerclasshelper) ou [UnregisterClassHelper](#unregisterclasshelper).

En spécifiant la macro [DECLARE_REGISTRY](registry-macros.md#declare_registry) , `UpdateRegistryClass` sera appelé automatiquement lors du traitement de votre mappage d’objet.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a> CComModule :: UpdateRegistryFromResourceD

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

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
dans Nom de ressource.

*nResID*<br/>
dans ID de ressource.

*bRegister*<br/>
dans Indique si l’objet doit être enregistré.

*pMapEntries*<br/>
dans Pointeur vers la table de remplacement qui stocke les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement `%MODULE%` . Pour utiliser des paramètres remplaçables supplémentaires, consultez les notes pour plus d’informations. Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Exécute le script contenu dans la ressource spécifiée par *lpszRes* ou *nResID*.

Si *bRegister* a la valeur true, cette méthode enregistre l’objet dans le registre système ; dans le cas contraire, il annule l’inscription de l’objet.

En spécifiant la macro [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) , est `UpdateRegistryFromResourceD` appelé automatiquement lors du traitement de votre mappage d’objets.

> [!NOTE]
> Pour remplacer les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la macro DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID. Au lieu de cela, créez un tableau de `_ATL_REGMAP_ENTRIES` structures, où chaque entrée contient un espace réservé de variable associé à une valeur pour remplacer l’espace réservé au moment de l’exécution. Appelez ensuite `UpdateRegistryFromResourceD` , en passant le tableau pour le paramètre *pMapEntries* . Cela ajoute toutes les valeurs de remplacement dans les `_ATL_REGMAP_ENTRIES` structures à la carte de remplacement du Bureau d’enregistrement.

> [!NOTE]
> Pour créer un lien statique vers le composant de Registre ATL, consultez [UpdateRegistryFromResourceS](#updateregistryfromresources).

Pour plus d’informations sur les paramètres et les scripts remplaçables, consultez l’article [composant du Registre ATL (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a> CComModule :: UpdateRegistryFromResourceS

À partir de ATL 7,0, `CComModule` est obsolète : pour plus d’informations, consultez [classes de module ATL](../../atl/atl-module-classes.md) .

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
dans Nom de ressource.

*nResID*<br/>
dans ID de ressource.

*bRegister*<br/>
dans Indique si le script de ressources doit être inscrit.

*pMapEntries*<br/>
dans Pointeur vers la table de remplacement qui stocke les valeurs associées aux paramètres remplaçables du script. ATL utilise automatiquement `%MODULE%` . Pour utiliser des paramètres remplaçables supplémentaires, consultez les notes pour plus d’informations. Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Semblable à [UpdateRegistryFromResourceD](#updateregistryfromresourced) Except `UpdateRegistryFromResourceS` crée un lien statique vers le composant de Registre ATL.

`UpdateRegistryFromResourceS` sera appelé automatiquement lors du traitement de votre mappage d’objet, à condition que vous l’ajoutiez `#define _ATL_STATIC_REGISTRY` à votre *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures).

> [!NOTE]
> Pour remplacer les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la macro [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) . Au lieu de cela, créez un tableau de `_ATL_REGMAP_ENTRIES` structures, où chaque entrée contient un espace réservé de variable associé à une valeur pour remplacer l’espace réservé au moment de l’exécution. Appelez ensuite `UpdateRegistryFromResourceS` , en passant le tableau pour le paramètre *pMapEntries* . Cela ajoute toutes les valeurs de remplacement dans les `_ATL_REGMAP_ENTRIES` structures à la carte de remplacement du Bureau d’enregistrement.

Pour plus d’informations sur les paramètres et les scripts remplaçables, consultez l’article [composant du Registre ATL (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
