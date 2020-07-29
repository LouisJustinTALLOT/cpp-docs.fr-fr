---
title: CComMultiThreadModelNoCS, classe
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
ms.openlocfilehash: beb5cd1e13de1a10546f28d4a7eb98e45b6e9af1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224264"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS, classe

`CComMultiThreadModelNoCS`fournit des méthodes thread-safe pour l’incrémentation et la décrémentation de la valeur d’une variable, sans verrouillage de section critique ou fonctionnalité de déverrouillage.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Référence la classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS :: CriticalSection](#criticalsection)|Référence la classe `CComFakeCriticalSection` .|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Référence la classe `CComMultiThreadModelNoCS` .|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS ::D Ecrement](#decrement)|Statique Décrémente la valeur de la variable spécifiée de manière thread-safe.|
|[CComMultiThreadModelNoCS :: incrément](#increment)|Statique Incrémente la valeur de la variable spécifiée de manière thread-safe.|

## <a name="remarks"></a>Notes

`CComMultiThreadModelNoCS`est semblable à [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en ce qu’il fournit des méthodes thread-safe pour l’incrémentation et la décrémentation d’une variable. Toutefois, lorsque vous référencez une classe de section critique par le biais de `CComMultiThreadModelNoCS` , les méthodes telles que `Lock` et ne `Unlock` font rien.

En général, vous utilisez `CComMultiThreadModelNoCS` le `ThreadModelNoCS` **`typedef`** nom. Cela **`typedef`** est défini dans `CComMultiThreadModelNoCS` , `CComMultiThreadModel` et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
> Les noms globaux **`typedef`** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) et [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) ne font pas référence `CComMultiThreadModelNoCS` .

En plus de `ThreadModelNoCS` , `CComMultiThreadModelNoCS` définit `AutoCriticalSection` et `CriticalSection` . Ces deux **`typedef`** noms font référence à [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associées à l’obtention et à la libération d’une section critique.

## <a name="requirements"></a>Spécifications

**En-tête :** atlbase. h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection

Lorsque vous utilisez `CComMultiThreadModelNoCS` , le **`typedef`** nom fait référence à la `AutoCriticalSection` classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas de section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions pour `AutoCriticalSection` . Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `AutoCriticalSection` :

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus de `AutoCriticalSection` , vous pouvez utiliser le **`typedef`** nom [CriticalSection](#criticalsection). Vous ne devez pas spécifier `AutoCriticalSection` dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel :: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS :: CriticalSection

Lorsque vous utilisez `CComMultiThreadModelNoCS` , le **`typedef`** nom fait référence à la `CriticalSection` classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Étant donné que `CComFakeCriticalSection` ne fournit pas de section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions pour `CriticalSection` . Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `CriticalSection` :

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus de `CriticalSection` , vous pouvez utiliser le **`typedef`** nom `AutoCriticalSection` . Vous ne devez pas spécifier `AutoCriticalSection` dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel :: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS ::D Ecrement

Cette fonction statique appelle la fonction Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), qui décrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de la décrémentation est 0, `Decrement` retourne 0. Si le résultat de la décrémentation est différent de zéro, la valeur de retour est également différente de zéro, mais peut ne pas être égale au résultat de la décrémentation.

### <a name="remarks"></a>Notes

**InterlockedDecrement** empêche plusieurs threads d’utiliser simultanément cette variable.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS :: incrément

Cette fonction statique appelle la fonction Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), qui incrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de l’incrément est 0, l' **incrément** retourne 0. Si le résultat de l’incrément est différent de zéro, la valeur de retour est également différente de zéro, mais peut ne pas être égale au résultat de l’incrémentation.

### <a name="remarks"></a>Notes

**InterlockedIncrement** empêche plusieurs threads d’utiliser simultanément cette variable.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

Lorsque `CComMultiThreadModelNoCS` vous utilisez, le **`typedef`** nom `ThreadModelNoCS` fait simplement référence à `CComMultiThreadModelNoCS` .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions pour `ThreadModelNoCS` . Le tableau suivant montre la relation entre la classe de modèle de thread et la classe référencée par `ThreadModelNoCS` :

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Notez que la définition de `ThreadModelNoCS` dans `CComMultiThreadModelNoCS` fournit une symétrie `CComMultiThreadModel` avec `CComSingleThreadModel` et. Par exemple, supposez que l’exemple de code dans a `CComMultiThreadModel::AutoCriticalSection` déclaré ce qui suit **`typedef`** :

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Quelle que soit la classe spécifiée pour `ThreadModel` (telle que `CComMultiThreadModelNoCS` ), est `_ThreadModel` résolu en conséquence.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel :: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
