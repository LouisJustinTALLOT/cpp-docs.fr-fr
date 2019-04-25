---
title: future, classe
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: 9ca18e62038d93a50b592868f71223962a22857d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159325"
---
# <a name="future-class"></a>future, classe

Décrit un *objet de retour asynchrone*.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Notes

Chaque *fournisseur asynchrone* standard retourne un objet dont le type est une instanciation de ce modèle. Un objet `future` fournit le seul accès au fournisseur asynchrone qui lui est associé. Si vous avez besoin de plusieurs objets de retour asynchrones associés au même fournisseur asynchrone, copiez l’objet `future` dans un objet [shared_future](../standard-library/shared-future-class.md).

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[future](#future)|Construit un objet `future`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get](#get)|Récupère le résultat stocké dans l’état asynchrone associé.|
|[share](#share)|Convertit l’objet en `shared_future`.|
|[valid](#valid)|Spécifie si l’objet n’est pas vide.|
|[wait](#wait)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.|
|[wait_for](#wait_for)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou que le délai spécifié soit écoulé.|
|[wait_until](#wait_until)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou jusqu’à un point spécifié dans le temps.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[future::operator=](#op_eq)|Transfère l’état asynchrone associé d’un objet spécifié.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<future >

**Espace de noms :** std

## <a name="future"></a>  future::future, constructeur

Construit un objet `future`.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autre*<br/>
Objet `future`.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet `future` sans état asynchrone associé.

Le deuxième constructeur construit un `future` de l’objet et transfère l’état asynchrone associé à partir de *autres*. *Autres* n’a plus d’état asynchrone associé.

## <a name="get"></a>  future::get

Récupère le résultat stocké dans l’état asynchrone associé.

```cpp
Ty get();
```

### <a name="return-value"></a>Valeur de retour

Si le résultat est une exception, la méthode la lève de nouveau. Sinon, le résultat est retourné.

### <a name="remarks"></a>Notes

Avant de récupérer le résultat, cette méthode bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.

Pour la spécialisation partielle `future<Ty&>`, la valeur stockée est une référence à l’objet qui a été passé au fournisseur asynchrone comme valeur de retour.

Car il n’existe aucune valeur stockée pour la spécialisation `future<void>`, la méthode retourne **void**.

Dans d’autres spécialisations, la méthode déplace sa valeur de retour à partir de la valeur stockée. Par conséquent, n’appelez cette méthode qu’une seule fois.

## <a name="op_eq"></a>  future::operator=

Transfère un état asynchrone associé d’un objet spécifié.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Droite*<br/>
Objet `future`.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Après le transfert, *droite* n’a plus d’état asynchrone associé.

## <a name="share"></a>  future::share

Convertit l’objet en un objet [shared_future](../standard-library/shared-future-class.md).

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Valeur de retour

`shared_future(move(*this))`

## <a name="valid"></a>  future::valid

Spécifie si l’objet a un état asynchrone associé.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valeur de retour

**true** si l’objet a un état asynchrone associé ; sinon, **false**.

## <a name="wait"></a>  future::wait

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Notes

Un état asynchrone associé est *prêt* uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="wait_for"></a>  future::wait_for

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou que l’intervalle de temps spécifié soit écoulé.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Paramètres

*Rel_time*<br/>
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie un intervalle de temps maximal pour le blocage du thread.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est prêt uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="wait_until"></a>  future::wait_until

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou jusqu’à un point spécifié dans le temps.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Paramètres

*Abs_time*<br/>
Objet [chrono::time_point](../standard-library/time-point-class.md) qui spécifie un point dans le temps après lequel le thread peut être débloqué.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est *prêt* uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
