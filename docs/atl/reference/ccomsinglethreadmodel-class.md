---
description: 'En savoir plus sur : classe CComSingleThreadModel'
title: CComSingleThreadModel, classe
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
ms.openlocfilehash: 42f1111590dd8e03a541ecc7a71b461e34a08f0b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142205"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel, classe

Cette classe fournit des méthodes pour incrémenter et décrémenter la valeur d’une variable.

## <a name="syntax"></a>Syntaxe

```
class CComSingleThreadModel
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Référence la classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel :: CriticalSection](#criticalsection)|Référence la classe `CComFakeCriticalSection` .|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Références `CComSingleThreadModel` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSingleThreadModel ::D Ecrement](#decrement)|Décrémente la valeur de la variable spécifiée. Cette implémentation n’est pas thread-safe.|
|[CComSingleThreadModel :: incrément](#increment)|Incrémente la valeur de la variable spécifiée. Cette implémentation n’est pas thread-safe.|

## <a name="remarks"></a>Notes

`CComSingleThreadModel` fournit des méthodes pour incrémenter et décrémenter la valeur d’une variable. Contrairement à [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ces méthodes ne sont pas thread-safe.

En général, vous utilisez `CComSingleThreadModel` l’un des deux **`typedef`** noms, [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). La classe référencée par chacune **`typedef`** dépend du modèle de thread utilisé, comme indiqué dans le tableau suivant :

|typedef|Modèle à thread unique|Modèle de thread cloisonné|Modèle de thread libre|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel` ; M = `CComMultiThreadModel`

`CComSingleThreadModel` définit lui-même trois **`typedef`** noms. `ThreadModelNoCS` références `CComSingleThreadModel` . `AutoCriticalSection` et de `CriticalSection` la classe de référence [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associées à l’obtention et à la libération de la propriété d’une section critique.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a> CComSingleThreadModel::AutoCriticalSection

Lorsque vous utilisez `CComSingleThreadModel` , le **`typedef`** nom fait référence à la `AutoCriticalSection` classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas de section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent des définitions pour `AutoCriticalSection` . Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `AutoCriticalSection` :

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus de `AutoCriticalSection` , vous pouvez utiliser le **`typedef`** nom [CriticalSection](#criticalsection). Vous ne devez pas spécifier `AutoCriticalSection` dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel :: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a> CComSingleThreadModel :: CriticalSection

Lorsque vous utilisez `CComSingleThreadModel` , le **`typedef`** nom fait référence à la `CriticalSection` classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas de section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent des définitions pour `CriticalSection` . Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `CriticalSection` :

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus de `CriticalSection` , vous pouvez utiliser le **`typedef`** nom [AutoCriticalSection](#autocriticalsection). Vous ne devez pas spécifier `AutoCriticalSection` dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel :: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a> CComSingleThreadModel ::D Ecrement

Cette fonction statique décrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers la variable à décrémenter.

### <a name="return-value"></a>Valeur renvoyée

Résultat de la décrémentation.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a> CComSingleThreadModel :: incrément

Cette fonction statique incrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers la variable à incrémenter.

### <a name="return-value"></a>Valeur renvoyée

Résultat de l’incrémentation.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a> CComSingleThreadModel::ThreadModelNoCS

Lorsque `CComSingleThreadModel` vous utilisez, le **`typedef`** nom `ThreadModelNoCS` fait simplement référence à `CComSingleThreadModel` .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent des définitions pour `ThreadModelNoCS` . Le tableau suivant montre la relation entre la classe de modèle de thread et la classe référencée par `ThreadModelNoCS` :

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel :: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
