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
ms.openlocfilehash: 01c7f953b6b8916394ee4c2b5b27cf84af52b920
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497084"
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
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Référence la `CComFakeCriticalSection`classe.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Référence la `CComMultiThreadModelNoCS`classe.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|Statique Décrémente la valeur de la variable spécifiée de manière thread-safe.|
|[CComMultiThreadModelNoCS::Increment](#increment)|Statique Incrémente la valeur de la variable spécifiée de manière thread-safe.|

## <a name="remarks"></a>Notes

`CComMultiThreadModelNoCS`est semblable à [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en ce qu’il fournit des méthodes thread-safe pour l’incrémentation et la décrémentation d’une variable. Toutefois, lorsque vous référencez une classe de section `CComMultiThreadModelNoCS`critique par le biais `Lock` de `Unlock` , les méthodes telles que et ne font rien.

En général, vous `CComMultiThreadModelNoCS` utilisez le `ThreadModelNoCS` nom de **typedef** . Ce **typedef** est défini dans `CComMultiThreadModelNoCS`, `CComMultiThreadModel`et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Les noms de **typedef** globaux [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) et [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) ne `CComMultiThreadModelNoCS`font pas référence.

En plus de `ThreadModelNoCS`, `CComMultiThreadModelNoCS` définit `AutoCriticalSection` et `CriticalSection`. Ces deux derniers noms **typedef** font référence à [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), qui fournit des méthodes vides associées à l’obtention et à la libération d’une section critique.

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

Lorsque vous `CComMultiThreadModelNoCS`utilisez, le nom `AutoCriticalSection` typedef fait référence à la classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

Étant `CComFakeCriticalSection` donné que ne fournit pas de section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions `AutoCriticalSection`pour. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `AutoCriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus de `AutoCriticalSection`, vous pouvez utiliser le nom typedef [CriticalSection](#criticalsection). Vous ne devez pas `AutoCriticalSection` spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemples

Consultez [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection

Lorsque vous `CComMultiThreadModelNoCS`utilisez, le nom `CriticalSection` typedef fait référence à la classe [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

Étant `CComFakeCriticalSection` donné que ne fournit pas de section critique, ses méthodes ne font rien.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions `CriticalSection`pour. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `CriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

En plus de `CriticalSection`, vous pouvez utiliser le nom `AutoCriticalSection`typedef. Vous ne devez pas `AutoCriticalSection` spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement

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

##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment

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

##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS

Lorsque vous `CComMultiThreadModelNoCS`utilisez, le nom `ThreadModelNoCS` de **typedef** fait simplement référence `CComMultiThreadModelNoCS`à.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) et [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) contiennent également des définitions `ThreadModelNoCS`pour. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe référencée `ThreadModelNoCS`par:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Notez que la définition de `ThreadModelNoCS` dans `CComMultiThreadModelNoCS` fournit une symétrie `CComMultiThreadModel` avec `CComSingleThreadModel`et. Par exemple, supposez que l’exemple `CComMultiThreadModel::AutoCriticalSection` de code dans a déclaré le **typedef**suivant:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Quelle que soit la classe spécifiée `ThreadModel` pour (telle `CComMultiThreadModelNoCS`que) `_ThreadModel` , est résolu en conséquence.

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
