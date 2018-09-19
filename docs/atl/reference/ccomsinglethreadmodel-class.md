---
title: CComSingleThreadModel, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: b257628747dca488292cfdfff0ef783303bd1b88
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094429"
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
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Référence de classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Référence de classe `CComFakeCriticalSection`.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Références `CComSingleThreadModel`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComSingleThreadModel::Decrement](#decrement)|Décrémente la valeur de la variable spécifiée. Cette implémentation n’est pas thread-safe.|
|[CComSingleThreadModel::Increment](#increment)|Incrémente la valeur de la variable spécifiée. Cette implémentation n’est pas thread-safe.|

## <a name="remarks"></a>Notes

`CComSingleThreadModel` Fournit des méthodes pour incrémenter et décrémenter la valeur d’une variable. Contrairement aux [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), ces méthodes ne sont pas thread-safe.  

En général, vous utilisez `CComSingleThreadModel` via un des deux **typedef** concernant les noms, soit [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). La classe référencée par chaque **typedef** varie selon le modèle de thread utilisé, comme indiqué dans le tableau suivant :  

|typedef|Modèle de thread unique|Modèle de thread apartment (cloisonné)|Modèle de thread libre|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` lui-même définit trois **typedef** noms. `ThreadModelNoCS` références `CComSingleThreadModel`. `AutoCriticalSection` et `CriticalSection` reference, classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associés à obtenir et de libérer de la propriété d’une section critique.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="autocriticalsection"></a>  CComSingleThreadModel::AutoCriticalSection

Lorsque vous utilisez `CComSingleThreadModel`, le **typedef** nom `AutoCriticalSection` fait référence à classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas d’une section critique, ses méthodes ne rien font.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent des définitions pour `AutoCriticalSection`. Le tableau suivant montre la relation entre la classe de modèle de thread et de la classe de section critique référencé par `AutoCriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus de `AutoCriticalSection`, vous pouvez utiliser la **typedef** nom [CriticalSection](#criticalsection). Vous ne devez pas spécifier `AutoCriticalSection` dans les objets globaux ou les membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComSingleThreadModel::CriticalSection

Lorsque vous utilisez `CComSingleThreadModel`, le **typedef** nom `CriticalSection` fait référence à classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas d’une section critique, ses méthodes ne rien font.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent des définitions pour `CriticalSection`. Le tableau suivant montre la relation entre la classe de modèle de thread et de la classe de section critique référencé par `CriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus de `CriticalSection`, vous pouvez utiliser la **typedef** nom [AutoCriticalSection](#autocriticalsection). Vous ne devez pas spécifier `AutoCriticalSection` dans les objets globaux ou les membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComSingleThreadModel::Decrement

Cette fonction statique décrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Pointeur vers la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Le résultat de la décrémentation.

##  <a name="increment"></a>  CComSingleThreadModel::Increment

Cette fonction statique décrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Pointeur vers la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Le résultat de l’incrément.

##  <a name="threadmodelnocs"></a>  CComSingleThreadModel::ThreadModelNoCS

Lorsque vous utilisez `CComSingleThreadModel`, le **typedef** nom `ThreadModelNoCS` fait simplement référence à `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contiennent des définitions pour `ThreadModelNoCS`. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe référencée par `ThreadModelNoCS`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
