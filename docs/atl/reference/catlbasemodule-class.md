---
title: CAtlBaseModule, classe
ms.date: 11/04/2016
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
ms.openlocfilehash: d57d6e631cb287496a4ff5516e97e65ec0152e30
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168291"
---
# <a name="catlbasemodule-class"></a>CAtlBaseModule, classe

Cette classe est instanciée dans chaque projet ATL.

## <a name="syntax"></a>Syntaxe

```cpp
class CAtlBaseModule : public _ATL_BASE_MODULE
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Ajoute une instance de ressource à la liste des handles stockés.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Retourne un handle vers une instance de ressource spécifiée.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Retourne l’instance de module à `CAtlBaseModule` partir d’un objet.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Retourne l’instance de ressource à `CAtlBaseModule` partir d’un objet.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Supprime une instance de ressource de la liste des descripteurs stockés.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Définit l’instance de ressource d' `CAtlBaseModule` un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlBaseModule :: m_bInitFailed](#m_binitfailed)|Variable qui indique si l’initialisation du module a échoué.|

## <a name="remarks"></a>Notes

Une instance de `CAtlBaseModule` nommée _AtlBaseModule est présente dans chaque projet ATL, contenant un handle vers l’instance de module, un handle vers le module contenant les ressources (qui, par défaut, sont un et le même) et un tableau de handles vers des modules fournissant des ressources principales. `CAtlBaseModule`peut être accessible en toute sécurité à partir de plusieurs threads.

Cette classe remplace la classe [CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcore. h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Ajoute une instance de ressource à la liste des handles stockés.

```cpp
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Paramètres

*hInst*<br/>
Instance de ressource à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si la ressource a été correctement ajoutée, false dans le cas contraire.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Constructeur.

```cpp
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Notes

Crée l'objet `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Retourne un handle vers une instance de ressource spécifiée.

```cpp
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Paramètres

*cliqu*<br/>
Numéro de l’instance de ressource.

### <a name="return-value"></a>Valeur de retour

Retourne le handle de l’instance de ressource, ou NULL s’il n’existe aucune instance de ressource correspondante.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Retourne l’instance de module à `CAtlBaseModule` partir d’un objet.

```cpp
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’instance de module.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Retourne l’instance de ressource.

```cpp
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’instance de ressource.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule :: m_bInitFailed

Variable qui indique si l’initialisation du module a échoué.

```cpp
static bool m_bInitFailed;
```

### <a name="remarks"></a>Notes

True si le module a été initialisé, false s’il n’a pas pu être initialisé.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Supprime une instance de ressource de la liste des descripteurs stockés.

```cpp
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Paramètres

*hInst*<br/>
Instance de ressource à supprimer.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si la ressource a été supprimée avec succès ; sinon, false.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Définit l’instance de ressource d' `CAtlBaseModule` un objet.

```cpp
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Paramètres

*hInst*<br/>
Nouvelle instance de ressource.

### <a name="return-value"></a>Valeur de retour

Retourne l’instance de ressource mise à jour.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de module](../../atl/atl-module-classes.md)
