---
title: CComMultiThreadModel, classe
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
ms.openlocfilehash: 74fb68eead498685ef252968124368863e27be75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497104"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel, classe

`CComMultiThreadModel`fournit des méthodes thread-safe pour l’incrémentation et la décrémentation de la valeur d’une variable.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModel
```

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Référence la classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Référence la classe [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Référence la classe [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|Statique Décrémente la valeur de la variable spécifiée de manière thread-safe.|
|[CComMultiThreadModel::Increment](#increment)|Statique Incrémente la valeur de la variable spécifiée de manière thread-safe.|

## <a name="remarks"></a>Notes

En général, vous `CComMultiThreadModel` utilisez l’un des deux noms **typedef** , soit [CComObjectThreadModel] (ATL-typedefs. MD # CComObjectThreadModel, soit [CComGlobalsThreadModel] (ATL-typedefs. MD # CComGlobalsThreadModel. La classe référencée par chaque **typedef** dépend du modèle de thread utilisé, comme indiqué dans le tableau suivant:

|typedef|Thread unique|Thread cloisonné|Thread libre|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

`CComMultiThreadModel`définit lui-même trois noms **typedef** . `AutoCriticalSection`et `CriticalSection` les classes de référence qui fournissent des méthodes pour obtenir et libérer la propriété d’une section critique. `ThreadModelNoCS`References, classe [CComMultiThreadModelNoCS (CComMultiThreadModelNoCS-class.md).

## <a name="requirements"></a>Configuration requise

**En-tête:** atlbase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

Lorsque vous `CComMultiThreadModel`utilisez, le nom `AutoCriticalSection` **typedef** fait référence à la classe [CComAutoCriticalSection](ccomautocriticalsection-class.md), qui fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Notes

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) et [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) contiennent également des définitions `AutoCriticalSection`pour. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `AutoCriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus de `AutoCriticalSection`, vous pouvez utiliser le nom typedef [CriticalSection](#criticalsection). Vous ne devez pas `AutoCriticalSection` spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemples

Le code suivant est modélisé après [CComObjectRootEx](ccomobjectrootex-class.md)et illustre `AutoCriticalSection` son utilisation dans un environnement de thread.

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

Les tableaux suivants présentent les résultats des `InternalAddRef` méthodes et `Lock` , en fonction du `ThreadModel` paramètre de modèle et du modèle de thread utilisé par l’application:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Méthode|Thread unique ou cloisonné|Thread libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|L’incrément n’est pas thread-safe.|L’incrément est thread-safe.|
|`Lock`|Ne fait rien. Il n’existe pas de section critique à verrouiller.|La section critique est verrouillée.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Méthode|Thread unique ou cloisonné|Thread libre|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|L’incrément n’est pas thread-safe.|L’incrément est thread-safe.|
|`Lock`|Ne fait rien. Il n’existe pas de section critique à verrouiller.|Ne fait rien. Il n’existe pas de section critique à verrouiller.|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

Lorsque vous `CComMultiThreadModel`utilisez, le nom `CriticalSection` **typedef** fait référence à la classe [CComCriticalSection](ccomcriticalsection-class.md), qui fournit des méthodes pour obtenir et libérer la propriété d’un objet de section critique.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Notes

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) et [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) contiennent également des définitions `CriticalSection`pour. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe de section critique référencée par `CriticalSection`:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

En plus de `CriticalSection`, vous pouvez utiliser le nom typedef [AutoCriticalSection](#autocriticalsection). Vous ne devez pas `AutoCriticalSection` spécifier dans des objets globaux ou des membres de classe statique si vous souhaitez éliminer le code de démarrage du CRT.

### <a name="example"></a>Exemples

Consultez [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

Cette fonction statique appelle la fonction Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), qui décrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers la variable à décrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de la décrémentation est 0, `Decrement` retourne 0. Si le résultat de la décrémentation est différent de zéro, la valeur de retour est également différente de zéro, mais peut ne pas être égale au résultat de la décrémentation.

### <a name="remarks"></a>Notes

`InterlockedDecrement`empêche plusieurs threads d’utiliser simultanément cette variable.

##  <a name="increment"></a>  CComMultiThreadModel::Increment

Cette fonction statique appelle la fonction Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), qui incrémente la valeur de la variable vers laquelle pointe *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Paramètres

*p*<br/>
dans Pointeur vers la variable à incrémenter.

### <a name="return-value"></a>Valeur de retour

Si le résultat de l’incrément est 0, `Increment` retourne 0. Si le résultat de l’incrément est différent de zéro, la valeur de retour est également différente de zéro, mais peut ne pas être égale au résultat de l’incrémentation.

### <a name="remarks"></a>Notes

`InterlockedIncrement`empêche plusieurs threads d’utiliser simultanément cette variable.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

Lorsque vous `CComMultiThreadModel`utilisez, le nom `ThreadModelNoCS` typedef fait référence à la classe [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Notes

`CComMultiThreadModelNoCS`fournit des méthodes thread-safe pour l’incrémentation et la décrémentation d’une variable; Toutefois, il ne fournit pas de section critique.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) et `CComMultiThreadModelNoCS` contiennent également des définitions `ThreadModelNoCS`pour. Le tableau suivant montre la relation entre la classe de modèle de thread et la classe référencée `ThreadModelNoCS`par:

|Classe définie dans|Classe référencée|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Exemple

Consultez [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Voir aussi

[CComSingleThreadModel, classe](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection, classe](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection, classe](ccomcriticalsection-class.md)<br/>
[Vue d’ensemble de la classe](../atl-class-overview.md)
