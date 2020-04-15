---
title: Classe CComSingleThreadModel
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327336"
---
# <a name="ccomsinglethreadmodel-class"></a>Classe CComSingleThreadModel

Cette classe fournit des méthodes pour incrémenter et décroisser la valeur d’une variable.

## <a name="syntax"></a>Syntaxe

```
class CComSingleThreadModel
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Références classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Classe `CComFakeCriticalSection`de références .|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Références `CComSingleThreadModel`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSingleThreadModel::Decrement](#decrement)|Décrète la valeur de la variable spécifiée. Cette implémentation n’est pas sans fil.|
|[CComSingleThreadModel::Increment](#increment)|Incréments la valeur de la variable spécifiée. Cette implémentation n’est pas sans fil.|

## <a name="remarks"></a>Notes

`CComSingleThreadModel`fournit des méthodes pour incrémenter et décroisser la valeur d’une variable. Contrairement à [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ces méthodes ne sont pas sans fil.

Typiquement, vous `CComSingleThreadModel` utilisez à travers l’un des deux noms **dactylographiés,** soit [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). La classe référencée par chaque **type** dépend du modèle de threading utilisé, comme indiqué dans le tableau suivant :

|typedef|Modèle de threading unique|Modèle de threading d’appartement|Modèle de threading gratuit|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`' ; M`CComMultiThreadModel`

`CComSingleThreadModel`définit lui-même trois noms **dactylographes.** `ThreadModelNoCS`références `CComSingleThreadModel`. `AutoCriticalSection`et `CriticalSection` la classe de référence [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associées à l’obtention et à la libération de la propriété d’une section critique.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

Lors `CComSingleThreadModel`de l’utilisation `AutoCriticalSection` , le nom **dactylographe** références classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Parce `CComFakeCriticalSection` que ne fournit pas une section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent `AutoCriticalSection`des définitions pour . Le tableau suivant montre la relation entre la classe de `AutoCriticalSection`modèle de threading et la classe de section critique référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus `AutoCriticalSection`de , vous pouvez utiliser le nom **de tapdef** [CriticalSection](#criticalsection). Vous ne `AutoCriticalSection` devez pas spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage CRT.

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CComSingleThreadModel::CriticalSection

Lors `CComSingleThreadModel`de l’utilisation `CriticalSection` , le nom **dactylographe** références classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Parce `CComFakeCriticalSection` que ne fournit pas une section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent `CriticalSection`des définitions pour . Le tableau suivant montre la relation entre la classe de `CriticalSection`modèle de threading et la classe de section critique référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus `CriticalSection`de , vous pouvez utiliser le nom **de tapdef** [AutoCriticalSection](#autocriticalsection). Vous ne `AutoCriticalSection` devez pas spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage CRT.

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::Decrement

Cette fonction statique décrément la valeur de la variable pointée par *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Pointeur sur la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Le résultat de la décroissation.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel::Increment

Cette fonction statique incrémente la valeur de la variable pointée par *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Pointeur sur la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’augmentation.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

Lors `CComSingleThreadModel`de l’utilisation `ThreadModelNoCS` , `CComSingleThreadModel`le nom **dactylographe** fait simplement référence .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent `ThreadModelNoCS`des définitions pour . Le tableau suivant montre la relation entre la classe `ThreadModelNoCS`de modèle de threading et la classe référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
