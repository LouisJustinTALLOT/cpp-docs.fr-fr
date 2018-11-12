---
title: Ccommultithreadmodelnocs, classe
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
ms.openlocfilehash: 5bad9ead5cb25d8ca1078bbbb25a00af1ebfcaa3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550759"
---
# <a name="ccommultithreadmodelnocs-class"></a>Ccommultithreadmodelnocs, classe

`CComMultiThreadModelNoCS` Fournit des méthodes de thread-safe pour incrémenter et décrémenter la valeur d’une variable, sans verrouillage de la section critique ou de fonctionnalités de déverrouillage.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Référence de classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Référence de classe `CComFakeCriticalSection`.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Référence de classe `CComMultiThreadModelNoCS`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statique) Décrémente la valeur de la variable spécifiée de manière thread-safe.|
|[CComMultiThreadModelNoCS::Increment](#increment)|(Statique) Incrémente la valeur de la variable spécifiée de manière thread-safe.|

## <a name="remarks"></a>Notes

`CComMultiThreadModelNoCS` est similaire à [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) car il fournit des méthodes de thread-safe pour incrémenter et décrémenter une variable. Toutefois, lorsque vous référencez une classe de section critique via `CComMultiThreadModelNoCS`, des méthodes telles que `Lock` et `Unlock` n’aura aucun effet.

En général, vous utilisez `CComMultiThreadModelNoCS` via la `ThreadModelNoCS` **typedef** nom. Cela **typedef** est défini dans `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Global **typedef** noms [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) et [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) ne font pas référence `CComMultiThreadModelNoCS`.

En plus de `ThreadModelNoCS`, `CComMultiThreadModelNoCS` définit `AutoCriticalSection` et `CriticalSection`. Ces deux derniers **typedef** noms font référence à [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associés à obtenir et de libérer une section critique.

## <a name="requirements"></a>Configuration requise

**En-tête :** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

Lorsque vous utilisez `CComMultiThreadModelNoCS`, le **typedef** nom `AutoCriticalSection` fait référence à classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas d’une section critique, ses méthodes ne rien font.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions pour `AutoCriticalSection`. Le tableau suivant montre la relation entre la classe de modèle de thread et de la classe de section critique référencé par `AutoCriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus de `AutoCriticalSection`, vous pouvez utiliser la **typedef** nom [CriticalSection](#criticalsection). Vous ne devez pas spécifier `AutoCriticalSection` dans les objets globaux ou les membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection

Lorsque vous utilisez `CComMultiThreadModelNoCS`, le **typedef** nom `CriticalSection` fait référence à classe [la classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas d’une section critique, ses méthodes ne rien font.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions pour `CriticalSection`. Le tableau suivant montre la relation entre la classe de modèle de thread et de la classe de section critique référencé par `CriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus de `CriticalSection`, vous pouvez utiliser la **typedef** nom `AutoCriticalSection`. Vous ne devez pas spécifier `AutoCriticalSection` dans les objets globaux ou les membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement

Cette fonction statique appelle la fonction Win32 [InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement), qui décrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Pointeur vers la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de la décrémentation est 0, puis `Decrement` retourne 0. Si le résultat de la décrémentation est différente de zéro, la valeur de retour est également différente de zéro mais ne peut-être pas égaler le résultat de la décrémentation.

### <a name="remarks"></a>Notes

**InterlockedDecrement** empêche que plusieurs threads simultanément à l’aide de cette variable.

##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment

Cette fonction statique appelle la fonction Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement), ce qui incrémente la valeur de la variable vers laquelle pointée *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
[in] Pointeur vers la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de l’incrément est 0, puis **incrément** retourne 0. Si le résultat de l’incrément est différente de zéro, la valeur de retour est également différente de zéro mais ne peut-être pas égaler le résultat de l’incrément.

### <a name="remarks"></a>Notes

**InterlockedIncrement** empêche que plusieurs threads simultanément à l’aide de cette variable.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS

Lorsque vous utilisez `CComMultiThreadModelNoCS`, le **typedef** nom `ThreadModelNoCS` fait simplement référence à `CComMultiThreadModelNoCS`.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions pour `ThreadModelNoCS`. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe référencée par `ThreadModelNoCS`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Notez que la définition de `ThreadModelNoCS` dans `CComMultiThreadModelNoCS` fournit une symétrie avec `CComMultiThreadModel` et `CComSingleThreadModel`. Par exemple, supposons que l’exemple de code dans `CComMultiThreadModel::AutoCriticalSection` déclaré ce qui suit **typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Quelle que soit la classe spécifiée pour `ThreadModel` (tel que `CComMultiThreadModelNoCS`), `_ThreadModel` résout en conséquence.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)