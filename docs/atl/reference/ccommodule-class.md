---
title: Classe CComModule
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
ms.openlocfilehash: 652c5f078ddbaf8d3e333f7003d6515a94dd8f83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327758"
---
# <a name="ccommodule-class"></a>Classe CComModule

À partir de ATL 7.0, `CComModule` est déprécié: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

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
|[CComModule::GetClassObject](#getclassobject)|Crée un objet d’un CLSID spécifié. Pour les LDL seulement.|
|[CComModule::GetModuleInstance](#getmoduleinstance)|Retourne `m_hInst`.|
|[CComModule::GetResourceInstance](#getresourceinstance)|Retourne `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Retourne `m_hInstTypeLib`.|
|[CComModule::Init](#init)|Initialise les membres des données.|
|[CComModule::RegisterClassHelper](#registerclasshelper)|Entre l’enregistrement standard de classe d’un objet dans le registre du système.|
|[CComModule::RegisterClassObjects](#registerclassobjects)|Enregistre l’objet de classe. Pour EXEs seulement.|
|[CComModule::RegisterServer](#registerserver)|Mise à jour du registre du système pour chaque objet dans la carte de l’objet.|
|[CComModule::RegisterTypeLib](#registertypelib)|Inscrit une bibliothèque de types.|
|[CComModule::RevokeClassObjects](#revokeclassobjects)|Révoque l’objet de classe. Pour EXEs seulement.|
|[CComModule::Terme](#term)|Communiqués aux membres des données.|
|[CComModule::UnregisterClassHelper](#unregisterclasshelper)|Supprime l’enregistrement standard de classe d’un objet du registre du système.|
|[CComModule::UnregisterServer](#unregisterserver)|Désenregistre chaque objet dans la carte de l’objet.|
|[CComModule::Mise à jourRegistryClasse](#updateregistryclass)|Enregistre ou non l’enregistrement de classe standard d’un objet.|
|[CComModule::UpdateRegistryDeResourceD](#updateregistryfromresourced)|Exécute le script contenu dans une ressource spécifiée pour enregistrer ou désinscrire un objet.|
|[CComModule::UpdateRegistryDeResourceS](#updateregistryfromresources)|Liens statiques vers le composant du registre ATL. Exécute le script contenu dans une ressource spécifiée pour enregistrer ou désinscrire un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CComModule::m_csObjMap](#m_csobjmap)|Assure un accès synchronisé aux informations de la carte des objets.|
|[CComModule::m_csTypeInfoHolder](#m_cstypeinfoholder)|Assure un accès synchronisé aux informations de type de bibliothèque.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Assure un accès synchronisé aux informations de classe de fenêtre et aux données statiques utilisées lors de la création de fenêtres.|
|[CComModule::m_hInst](#m_hinst)|Contient la poignée à l’instance du module.|
|[CComModule::m_hInstResource](#m_hinstresource)|Par défaut, contient la poignée à l’instance du module.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|Par défaut, contient la poignée à l’instance du module.|
|[CComModule::m_pObjMap](#m_pobjmap)|Points à la carte de l’objet maintenu par l’instance du module.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Cette classe est dépréciée, et les assistants de génération de code ATL utilisent maintenant les classes [dérivées CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) et [CAtlModule.](../../atl/reference/catlmodule-class.md) Voir [les classes de module ATL](../../atl/atl-module-classes.md) pour plus d’informations. Les informations qui suivent sont destinées à une utilisation avec des applications créées avec des versions plus anciennes d’ATL. `CComModule`fait toujours partie d’ATL pour la capacité à l’envers.

`CComModule`implémente un module serveur COM, permettant à un client d’accéder aux composants du module. `CComModule`prend en charge les modules DLL (en cours de traitement) et EXE (local).

Une `CComModule` instance utilise une carte d’objet pour maintenir un ensemble de définitions d’objets de classe. Cette carte d’objet est `_ATL_OBJMAP_ENTRY` implémentée comme un tableau de structures, et contient des informations pour :

- Saisie et suppression des descriptions d’objets dans le registre du système.

- Instantané des objets à travers une usine de classe.

- Établir la communication entre un client et l’objet racine dans le composant.

- Exécution de la gestion à vie des objets de classe.

Lorsque vous exécutez l’AppWizard ATL `_Module`COM, l’assistant génère automatiquement , une instance globale ou `CComModule` une classe dérivée de celui-ci. Pour plus d’informations sur le assistant de projet ATL, voir l’article [Création d’un projet ATL](../../atl/reference/creating-an-atl-project.md).

En plus `CComModule`de , ATL fournit [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md), qui implémente un module de modèle d’appartement pour les EXEs et les services Windows. Dérivez votre `CComAutoThreadModule` module à partir de quand vous voulez créer des objets dans plusieurs appartements.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a>CComModule::GetClassObject

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Paramètres

*rclsid*<br/>
[dans] Le CLSID de l’objet à créer.

*riid*<br/>
[dans] L’IID de l’interface demandée.

*Ppv*<br/>
[out] Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppv* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Crée un objet du CLSID spécifié et récupère un pointeur d’interface sur cet objet.

`GetClassObject`n’est disponible que pour les LDL.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CComModule::GetModuleInstance

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

Le HINSTANCE identifiant ce module.

### <a name="remarks"></a>Notes

Renvoie [le](#m_hinst) m_hInst membre des données.

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a>CComModule::GetResourceInstance

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

Un HINSTANCE.

### <a name="remarks"></a>Notes

Renvoie le membre [m_hInstResource](#m_hinstresource) de données.

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a>CComModule::GetTypeLibInstance

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Valeur de retour

Un HINSTANCE.

### <a name="remarks"></a>Notes

Renvoie [le](#m_hinsttypelib) m_hInstTypeLib membre des données.

## <a name="ccommoduleinit"></a><a name="init"></a>CComModule::Init

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Un pointeur à un tableau d’entrées de carte d’objet.

*h*<br/>
[dans] Le HINSTANCE `DLLMain` est `WinMain`passé à ou .

*plibid*<br/>
[dans] Un pointeur pour le LIBID de la bibliothèque de type associée au projet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Initialise tous les membres des données.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a>CComModule::m_csObjMap

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Notes

Assure un accès synchronisé à la carte des objets.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a>CComModule::m_csTypeInfoHolder

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Notes

Assure un accès synchronisé à la bibliothèque type.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a>CComModule::m_csWindowCreate

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Notes

Assure un accès synchronisé aux informations de classe de fenêtre et aux données statiques utilisées lors de la création de fenêtres.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a>CComModule::m_hInst

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Notes

Contient la poignée à l’instance du module.

La méthode [Init](#init) se `m_hInst` fixe `DLLMain` `WinMain`à la poignée passée à ou .

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a>CComModule::m_hInstResource

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Notes

Par défaut, contient la poignée à l’instance du module.

La méthode [Init](#init) se `m_hInstResource` fixe `DLLMain` `WinMain`à la poignée passée à ou . Vous pouvez `m_hInstResource` vous définir explicitement à la poignée d’une ressource.

La méthode [GetResourceInstance](#getresourceinstance) renvoie `m_hInstResource`la poignée stockée dans .

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a>CComModule::m_hInstTypeLib

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Notes

Par défaut, contient la poignée à l’instance du module.

La méthode [Init](#init) se `m_hInstTypeLib` fixe `DLLMain` `WinMain`à la poignée passée à ou . Vous pouvez `m_hInstTypeLib` vous définir explicitement à la poignée d’une bibliothèque type.

La méthode [GetTypeLibInstance](#gettypelibinstance) renvoie `m_hInstTypeLib`la poignée stockée dans .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a>CComModule::m_pObjMap

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Notes

Points à la carte de l’objet maintenu par l’instance du module.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a>CComModule::RegisterClassHelper

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

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
[dans] Le CLSID de l’objet à enregistrer.

*lpszProgID*<br/>
[dans] Le ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
[dans] La version indépendante ProgID associée à l’objet.

*nDescID (en)*<br/>
[dans] L’identifiant d’une ressource de chaîne pour la description de l’objet.

*dwFlags*<br/>
[dans] Spécifie le modèle de threading pour entrer dans le registre. Les valeurs possibles sont THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Entre l’enregistrement standard de classe d’un objet dans le registre du système.

La [méthode UpdateRegistryClass](#updateregistryclass) appelle `RegisterClassHelper`.

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a>CComModule::RegisterClassObjects

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Paramètres

*dwClsContexte*<br/>
[dans] Spécifie le contexte dans lequel l’objet de classe doit être exécuté. Les valeurs possibles sont CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER ou CLSCTX_LOCAL_SERVER. Pour une description de ces valeurs, voir [CLSCTX](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) dans le SDK Windows.

*dwFlags*<br/>
[dans] Détermine les types de connexion à l’objet de classe. Les valeurs possibles sont REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE ou REGCLS_MULTI_SEPARATE. Pour une description de ces valeurs, voir [REGCLS](/windows/win32/api/combaseapi/ne-combaseapi-regcls) dans le SDK Windows.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Enregistre un objet de classe EXE avec OLE afin que d’autres applications puissent s’y connecter. Cette méthode n’est disponible que pour les EXE.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a>CComModule::RegisterServer

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Paramètres

*bRegTypeLib*<br/>
[dans] Indique si la bibliothèque type sera enregistrée. La valeur par défaut est FALSE.

*pCLSID (en)*<br/>
[dans] Indique le CLSID de l’objet à enregistrer. Si NULL (la valeur par défaut), tous les objets de la carte de l’objet seront enregistrés.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Selon le paramètre *pCLSID,* met à jour le registre du système pour un seul objet de classe ou pour tous les objets de la carte des objets.

Si *bRegTypeLib* est VRAI, les informations de bibliothèque type seront également mises à jour.

Voir [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour obtenir des informations sur la façon d’ajouter une entrée à la carte des objets.

`RegisterServer`sera appelé automatiquement `DLLRegisterServer` par pour un `WinMain` DLL ou par `/RegServer` pour une exécution EXE avec l’option de ligne de commande.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a>CComModule::RegisterTypeLib

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Paramètres

*lpszIndex*<br/>
[dans] Chaîne dans `"\\N"`le `N` format , où est l’indice integer de la ressource TYPELIB.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Ajoute de l’information sur une bibliothèque type au registre du système.

Si l’instance du module contient plusieurs bibliothèques de type, utilisez la deuxième version de cette méthode pour spécifier le type de bibliothèque à utiliser.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a>CComModule::RevokeClassObjects

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Enlève l’objet de classe. Cette méthode n’est disponible que pour les EXE.

## <a name="ccommoduleterm"></a><a name="term"></a>CComModule::Terme

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
void Term() throw();
```

### <a name="remarks"></a>Notes

Communiqués à tous les membres des données.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a>CComModule::UnregisterClassHelper

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
[dans] Le CLSID de l’objet à non enregistré.

*lpszProgID*<br/>
[dans] Le ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
[dans] La version indépendante ProgID associée à l’objet.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Supprime l’enregistrement standard de classe d’un objet du registre du système.

La [méthode UpdateRegistryClass](#updateregistryclass) appelle `UnregisterClassHelper`.

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a>CComModule::UnregisterServer

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Paramètres

*bUnRegTypeLib*<br/>
Si VRAI, la bibliothèque de type n’est pas non enregistrée.

*pCLSID (en)*<br/>
Indique que le CLSID de l’objet n’est pas enregistré. Si NULL (la valeur par défaut), tous les objets de la carte de l’objet ne seront pas enregistrés.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Selon le paramètre *pCLSID,* non enregistré soit un objet de classe unique ou tous les objets de la carte des objets.

`UnregisterServer`sera appelé automatiquement `DLLUnregisterServer` par pour un `WinMain` DLL ou par `/UnregServer` pour une exécution EXE avec l’option de ligne de commande.

Voir [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) pour obtenir des informations sur la façon d’ajouter une entrée à la carte des objets.

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a>CComModule::Mise à jourRegistryClasse

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

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
Le CLSID de l’objet à enregistrer ou non enregistré.

*lpszProgID*<br/>
Le ProgID associé à l’objet.

*lpszVerIndProgID*<br/>
La version indépendante ProgID associée à l’objet.

*nDescID (en)*<br/>
L’identifiant de la ressource de chaîne pour la description de l’objet.

*szDesc*<br/>
Une chaîne contenant la description de l’objet.

*dwFlags*<br/>
Spécifie le modèle de threading pour entrer dans le registre. Les valeurs possibles sont THREADFLAGS_APARTMENT, THREADFLAGS_BOTH ou AUTPRXFLAG.

*bRegister (en)*<br/>
Indique si l’objet doit être enregistré.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Si *bRegister* est VRAI, cette méthode entre l’enregistrement de classe standard de l’objet dans le registre du système.

Si *bRegister* est FALSE, il supprime l’enregistrement de l’objet.

Selon la valeur de *bRegister*, `UpdateRegistryClass` appels soit [RegisterClassHelper](#registerclasshelper) ou [UnregisterClassHelper](#unregisterclasshelper).

En spécifiant la [DECLARE_REGISTRY](registry-macros.md#declare_registry) macro, `UpdateRegistryClass` sera invoqué automatiquement lorsque votre carte d’objet est traitée.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a>CComModule::UpdateRegistryDeResourceD

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

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
[dans] Un nom de ressource.

*nResID (en)*<br/>
[dans] Une pièce d’identité de ressource.

*bRegister (en)*<br/>
[dans] Indique si l’objet doit être enregistré.

*pMapEntries (en)*<br/>
[dans] Un pointeur sur la carte de remplacement stockant les valeurs associées aux paramètres remplaçables du script. ATL utilise `%MODULE%`automatiquement . Pour utiliser d’autres paramètres remplaçables, consultez les Remarques pour plus de détails. Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Exécute le script contenu dans la ressource spécifiée par *lpszRes* ou *nResID*.

Si *bRegister* est VRAI, cette méthode enregistre l’objet dans le registre du système; autrement, il déenregistre l’objet.

En spécifiant le [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) `UpdateRegistryFromResourceD` macro, sera invoqué automatiquement lorsque votre carte d’objet est traitée.

> [!NOTE]
> Pour remplacer les valeurs de remplacement au moment de l’exécution, ne spécifiez pas le DECLARE_REGISTRY_RESOURCE ou DECLARE_REGISTRY_RESOURCEID macro. Au lieu de `_ATL_REGMAP_ENTRIES` cela, créer un tableau de structures, où chaque entrée contient un espace variable avec une valeur pour remplacer le placeholder au moment de l’exécution. Ensuite, `UpdateRegistryFromResourceD`appelez, en passant le tableau pour le paramètre *pMapEntries.* Cela ajoute toutes les `_ATL_REGMAP_ENTRIES` valeurs de remplacement dans les structures à la carte de remplacement du registraire.

> [!NOTE]
> Pour établir un lien statique vers le composant du registre ATL (registraire), voir [UpdateRegistryFromResourceS](#updateregistryfromresources).

Pour plus d’informations sur les paramètres remplaçables et le script, voir l’article [The ATL Registry Component (registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a>CComModule::UpdateRegistryDeResourceS

En date de ATL 7.0, `CComModule` est obsolète: voir [ATL Module Classes](../../atl/atl-module-classes.md) pour plus de détails.

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
[dans] Un nom de ressource.

*nResID (en)*<br/>
[dans] Une pièce d’identité de ressource.

*bRegister (en)*<br/>
[dans] Indique si le script de ressource doit être enregistré.

*pMapEntries (en)*<br/>
[dans] Un pointeur sur la carte de remplacement stockant les valeurs associées aux paramètres remplaçables du script. ATL utilise `%MODULE%`automatiquement . Pour utiliser d’autres paramètres remplaçables, consultez les Remarques pour plus de détails. Sinon, utilisez la valeur par défaut NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Semblable à [UpdateRegistryDeResourceD,](#updateregistryfromresourced) sauf `UpdateRegistryFromResourceS` crée un lien statique vers le composant du registre ATL (registraire).

`UpdateRegistryFromResourceS`seront invoqués automatiquement lorsque votre carte d’objet est traitée, à condition que vous ajoutiez `#define _ATL_STATIC_REGISTRY` à votre *pch.h* (*stdafx.h* dans Visual Studio 2017 et plus tôt).

> [!NOTE]
> Pour remplacer les valeurs de remplacement au moment de l’exécution, ne spécifiez pas la [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) ou [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) macro. Au lieu de `_ATL_REGMAP_ENTRIES` cela, créer un tableau de structures, où chaque entrée contient un espace variable avec une valeur pour remplacer le placeholder au moment de l’exécution. Ensuite, `UpdateRegistryFromResourceS`appelez, en passant le tableau pour le paramètre *pMapEntries.* Cela ajoute toutes les `_ATL_REGMAP_ENTRIES` valeurs de remplacement dans les structures à la carte de remplacement du registraire.

Pour plus d’informations sur les paramètres remplaçables et le script, voir l’article [The ATL Registry Component (registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
