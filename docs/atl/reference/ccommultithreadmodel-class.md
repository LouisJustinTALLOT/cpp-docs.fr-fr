---
title: Classe CComMultiThreadModel
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327669"
---
# <a name="ccommultithreadmodel-class"></a>Classe CComMultiThreadModel

`CComMultiThreadModel`fournit des méthodes sans fil pour incrémenter et décroisser la valeur d’une variable.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModel
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Références classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Références classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Références classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|(Statique) Décrète la valeur de la variable spécifiée d’une manière sans fil.|
|[CComMultiThreadModel::Increment](#increment)|(Statique) Incréments la valeur de la variable spécifiée d’une manière sans fil.|

## <a name="remarks"></a>Notes

Typiquement, vous `CComMultiThreadModel` utilisez par l’un des deux noms **dactylographiés,** soit [CComObjectThreadModel] (atl-typedefs.md-ccomobjectthreadmodel ou [CComGlobalsThreadModel] (atl-typedefs.md-ccomglobalsthreadmodel. La classe référencée par chaque **type** dépend du modèle de threading utilisé, comme indiqué dans le tableau suivant :

|typedef|Filet unique|Threading appartement|Threading gratuit|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`' ; M`CComMultiThreadModel`

`CComMultiThreadModel`définit lui-même trois noms **dactylographes.** `AutoCriticalSection`et `CriticalSection` des cours de référence qui fournissent des méthodes pour obtenir et libérer la propriété d’une section critique. `ThreadModelNoCS`classe de références [CComMultiThreadModelNoCS (ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Spécifications

**En-tête:** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

Lors `CComMultiThreadModel`de l’utilisation `AutoCriticalSection` , le nom **dactylographié** référence classe [CComAutoCriticalSection](ccomautocriticalsection-class.md), qui fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) et [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) contiennent `AutoCriticalSection`également des définitions pour . Le tableau suivant montre la relation entre la classe de `AutoCriticalSection`modèle de threading et la classe de section critique référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus `AutoCriticalSection`de , vous pouvez utiliser le nom **de tapdef** [CriticalSection](#criticalsection). Vous ne `AutoCriticalSection` devez pas spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage CRT.

### <a name="example"></a>Exemple

Le code suivant est calqué sur [CComObjectRootEx](ccomobjectrootex-class.md), et démontre `AutoCriticalSection` être utilisé dans un environnement de filetage.

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

Les tableaux suivants montrent `InternalAddRef` les `Lock` résultats de `ThreadModel` la et des méthodes, en fonction du paramètre du modèle et du modèle de threading utilisé par l’application :

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel - CComObjectThreadModel

|Méthode|Threading simple ou appartement|Threading gratuit|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|L’incrément n’est pas sans fil.|L’incrément est sans fil.|
|`Lock`|Ne fait rien; il n’y a pas de section critique à verrouiller.|La section critique est verrouillée.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel - CComObjectThreadModel::ThreadModelNoCS

|Méthode|Threading simple ou appartement|Threading gratuit|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|L’incrément n’est pas sans fil.|L’incrément est sans fil.|
|`Lock`|Ne fait rien; il n’y a pas de section critique à verrouiller.|Ne fait rien; il n’y a pas de section critique à verrouiller.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModel::CriticalSection

Lors `CComMultiThreadModel`de l’utilisation `CriticalSection` , le nom **dactylographié** fait référence à la classe [CComCriticalSection](ccomcriticalsection-class.md), qui fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) et [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) contiennent `CriticalSection`également des définitions pour . Le tableau suivant montre la relation entre la classe de `CriticalSection`modèle de threading et la classe de section critique référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus `CriticalSection`de , vous pouvez utiliser le nom **de tapdef** [AutoCriticalSection](#autocriticalsection). Vous ne `AutoCriticalSection` devez pas spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage CRT.

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::Decrement

Cette fonction statique appelle la fonction Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), qui décrément la valeur de la variable pointée par *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Pointeur sur la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de la décroissement est de 0, puis `Decrement` retourne 0. Si le résultat de la décroissement n’est paszero, la valeur de rendement est également nonzero mais peut ne pas égaler le résultat de la décroissation.

### <a name="remarks"></a>Notes

`InterlockedDecrement`empêche plus d’un thread d’utiliser simultanément cette variable.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel::Increment

Cette fonction statique appelle la fonction Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), qui incrémente la valeur de la variable pointée par *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Paramètres

*P*<br/>
[dans] Pointeur sur la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de l’incrément `Increment` est de 0, puis retourne 0. Si le résultat de l’augmentation n’est paszero, la valeur de retour est également nonzero mais peut ne pas égaler le résultat de l’augmentation.

### <a name="remarks"></a>Notes

`InterlockedIncrement`empêche plus d’un thread d’utiliser simultanément cette variable.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

Lors `CComMultiThreadModel`de l’utilisation `ThreadModelNoCS` , le nom **dactylographier** référence classe [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

`CComMultiThreadModelNoCS`fournit des méthodes sans fil pour l’incrémentation et la décroissation d’une variable; toutefois, il ne fournit pas de section critique.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) `CComMultiThreadModelNoCS` et contiennent également `ThreadModelNoCS`des définitions pour . Le tableau suivant montre la relation entre la classe `ThreadModelNoCS`de modèle de threading et la classe référencée par :

|Catégorie définie en|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Exemple

Voir [CComMultiThreadModel:AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[Classe CComSingleThreadModel](ccomsinglethreadmodel-class.md)<br/>
[Classe CComAutoCriticalSection](ccomautocriticalsection-class.md)<br/>
[Classe CComCriticalSection](ccomcriticalsection-class.md)<br/>
[Vue d'ensemble des classes](../atl-class-overview.md)
