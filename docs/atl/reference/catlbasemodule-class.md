---
title: Classe CAtlBaseModule
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
ms.openlocfilehash: a55412eff18fd04ac4e41c0f001991c1cf725b9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321508"
---
# <a name="catlbasemodule-class"></a>Classe CAtlBaseModule

Cette classe est instantanée dans chaque projet ATL.

## <a name="syntax"></a>Syntaxe

```
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
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Ajoute une instance de ressources à la liste des poignées stockées.|
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Renvoie une poignée à une instance de ressources spécifiée.|
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Renvoie l’instance `CAtlBaseModule` du module à partir d’un objet.|
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Renvoie l’instance `CAtlBaseModule` de ressource d’un objet.|
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Supprime une instance de ressources de la liste des poignées stockées.|
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Définit l’instance `CAtlBaseModule` de ressources d’un objet.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Une variable qui indique si l’initialisation du module a échoué.|

## <a name="remarks"></a>Notes

Un exemple `CAtlBaseModule` de _AtlBaseModule nommé est présent dans chaque projet ATL, contenant une poignée à l’instance du module, une poignée au module contenant des ressources (qui par défaut, sont un seul et même), et un tableau de poignées aux modules fournissant des ressources primaires. `CAtlBaseModule`est accessible en toute sécurité à partir de plusieurs threads.

Cette classe remplace la classe [CComModule](../../atl/reference/ccommodule-class.md) obsolète utilisée dans les versions antérieures d’ATL.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)

`CAtlBaseModule`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcore.h

## <a name="catlbasemoduleaddresourceinstance"></a><a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance

Ajoute une instance de ressources à la liste des poignées stockées.

```
bool AddResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Paramètres

*hInst*<br/>
L’exemple de ressource à ajouter.

### <a name="return-value"></a>Valeur de retour

Rendements vrais si la ressource a été ajoutée avec succès, faux autrement.

## <a name="catlbasemodulecatlbasemodule"></a><a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule

Constructeur.

```
CAtlBaseModule() throw();
```

### <a name="remarks"></a>Notes

Crée l'objet `CAtlBaseModule`.

## <a name="catlbasemodulegethinstanceat"></a><a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt

Renvoie une poignée à une instance de ressources spécifiée.

```
HINSTANCE GetHInstanceAt(int i) throw();
```

### <a name="parameters"></a>Paramètres

*Ⅰ*<br/>
Le nombre de l’instance de ressource.

### <a name="return-value"></a>Valeur de retour

Renvoie la poignée à l’instance de ressources, ou NULL si il n’existe pas d’instance de ressources correspondante.

## <a name="catlbasemodulegetmoduleinstance"></a><a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance

Renvoie l’instance `CAtlBaseModule` du module à partir d’un objet.

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’instance du module.

## <a name="catlbasemodulegetresourceinstance"></a><a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance

Retourne l’exemple de ressource.

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne l’exemple de ressource.

## <a name="catlbasemodulem_binitfailed"></a><a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed

Une variable qui indique si l’initialisation du module a échoué.

```
static bool m_bInitFailed;
```

### <a name="remarks"></a>Notes

Vrai si le module a para paradé, faux s’il n’a pas réussi à initialiser.

## <a name="catlbasemoduleremoveresourceinstance"></a><a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance

Supprime une instance de ressources de la liste des poignées stockées.

```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Paramètres

*hInst*<br/>
L’instance de ressources à supprimer.

### <a name="return-value"></a>Valeur de retour

Rendements vrais si la ressource a été enlevée avec succès, faux autrement.

## <a name="catlbasemodulesetresourceinstance"></a><a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance

Définit l’instance `CAtlBaseModule` de ressources d’un objet.

```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```

### <a name="parameters"></a>Paramètres

*hInst*<br/>
La nouvelle instance des ressources.

### <a name="return-value"></a>Valeur de retour

Retourne l’instance de ressources mise à jour.

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)<br/>
[Classes de modules](../../atl/atl-module-classes.md)
