---
title: Classe CComMultiThreadModelNoCS
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327650"
---
# <a name="ccommultithreadmodelnocs-class"></a>Classe CComMultiThreadModelNoCS

`CComMultiThreadModelNoCS`fournit des méthodes sans fil pour incrémenter et décroisser la valeur d’une variable, sans fonctionnalité critique de verrouillage de section ou de déverrouillage.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Références classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Classe `CComFakeCriticalSection`de références .|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Classe `CComMultiThreadModelNoCS`de références .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statique) Décrète la valeur de la variable spécifiée d’une manière sans fil.|
|[CComMultiThreadModelNoCS::Increment](#increment)|(Statique) Incréments la valeur de la variable spécifiée d’une manière sans fil.|

## <a name="remarks"></a>Notes

`CComMultiThreadModelNoCS`est similaire à [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en ce qu’il fournit des méthodes sans fil pour incrémenter et décimer une variable. Cependant, lorsque vous faites référence `CComMultiThreadModelNoCS`à une `Lock` `Unlock` classe de section critique à travers , des méthodes telles que et ne fera rien.

Typiquement, vous `CComMultiThreadModelNoCS` utilisez `ThreadModelNoCS` à travers le nom **dactylographe.** Ce **typedef** est `CComMultiThreadModelNoCS` `CComMultiThreadModel`défini en , , et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
> Les noms de **typedef** global [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) et [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) ne font pas référence `CComMultiThreadModelNoCS`.

En plus `ThreadModelNoCS` `CComMultiThreadModelNoCS` de `AutoCriticalSection` , `CriticalSection`définit et . Ces deux derniers noms **typés font** référence [à CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associées à l’obtention et à la libération d’une section critique.

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

Lors `CComMultiThreadModelNoCS`de l’utilisation `AutoCriticalSection` , le nom **dactylographe** références classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Parce `CComFakeCriticalSection` que ne fournit pas une section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent `AutoCriticalSection`également des définitions pour . Le tableau suivant montre la relation entre la classe de `AutoCriticalSection`modèle de threading et la classe de section critique référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus `AutoCriticalSection`de , vous pouvez utiliser le nom **de tapdef** [CriticalSection](#criticalsection). Vous ne `AutoCriticalSection` devez pas spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage CRT.

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection

Lors `CComMultiThreadModelNoCS`de l’utilisation `CriticalSection` , le nom **dactylographe** références classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Parce `CComFakeCriticalSection` que ne fournit pas une section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent `CriticalSection`également des définitions pour . Le tableau suivant montre la relation entre la classe de `CriticalSection`modèle de threading et la classe de section critique référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus `CriticalSection`de , vous pouvez `AutoCriticalSection`utiliser le nom **dactylographe** . Vous ne `AutoCriticalSection` devez pas spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage CRT.

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Decrement

Cette fonction statique appelle la fonction Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), qui décrément la valeur de la variable pointée par *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Pointeur sur la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de la décroissement est de 0, puis `Decrement` retourne 0. Si le résultat de la décroissement n’est paszero, la valeur de rendement est également nonzero mais peut ne pas égaler le résultat de la décroissation.

### <a name="remarks"></a>Notes

**InterlockedDecrement** empêche plus d’un thread d’utiliser simultanément cette variable.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Increment

Cette fonction statique appelle la fonction Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), qui incrémente la valeur de la variable pointée par *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Pointeur sur la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de l’incrément est de 0, puis **Increment** retourne 0. Si le résultat de l’augmentation n’est paszero, la valeur de retour est également nonzero mais peut ne pas égaler le résultat de l’augmentation.

### <a name="remarks"></a>Notes

**InterlockedIncrement** empêche plus d’un thread d’utiliser simultanément cette variable.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

Lors `CComMultiThreadModelNoCS`de l’utilisation `ThreadModelNoCS` , `CComMultiThreadModelNoCS`le nom **dactylographe** fait simplement référence .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent `ThreadModelNoCS`également des définitions pour . Le tableau suivant montre la relation entre la classe `ThreadModelNoCS`de modèle de threading et la classe référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Notez que `ThreadModelNoCS` la `CComMultiThreadModelNoCS` définition de `CComMultiThreadModel` dans `CComSingleThreadModel`fournit la symétrie avec et . Supposons, par exemple, `CComMultiThreadModel::AutoCriticalSection` le code de l’échantillon dans déclaré le **type suivant**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Indépendamment de la `ThreadModel` classe spécifiée pour (comme `CComMultiThreadModelNoCS`), `_ThreadModel` se résout en conséquence.

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
