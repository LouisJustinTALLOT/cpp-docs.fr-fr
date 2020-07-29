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
ms.openlocfilehash: ac52429919f83a90a87141399952e248e18e0862
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220936"
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
|[postérieur](#future)|Construit un objet `future`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[get](#get)|Récupère le résultat stocké dans l’état asynchrone associé.|
|[partager](#share)|Convertit l’objet en `shared_future`.|
|[valide](#valid)|Spécifie si l’objet n’est pas vide.|
|[qu'](#wait)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.|
|[wait_for](#wait_for)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou que le délai spécifié soit écoulé.|
|[wait_until](#wait_until)|Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt ou jusqu’à un point spécifié dans le temps.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[future::operator=](#op_eq)|Transfère l’état asynchrone associé d’un objet spécifié.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<future>

**Espace de noms :** std

## <a name="futurefuture-constructor"></a><a name="future"></a>futur :: future, constructeur

Construit un objet `future`.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Paramètres

*Autres*\
Objet `future`.

### <a name="remarks"></a>Notes

Le premier constructeur construit un objet `future` sans état asynchrone associé.

Le deuxième constructeur construit un `future` objet et transfère l’état asynchrone associé à partir d' *autres*. D' *autres* n’ont plus d’état asynchrone associé.

## <a name="futureget"></a><a name="get"></a>à venir :: obtient

Récupère le résultat stocké dans l’état asynchrone associé.

```cpp
Ty get();
```

### <a name="return-value"></a>Valeur de retour

Si le résultat est une exception, la méthode la lève de nouveau. Sinon, le résultat est retourné.

### <a name="remarks"></a>Notes

Avant de récupérer le résultat, cette méthode bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit prêt.

Pour la spécialisation partielle `future<Ty&>`, la valeur stockée est une référence à l’objet qui a été passé au fournisseur asynchrone comme valeur de retour.

Étant donné qu’il n’existe aucune valeur stockée pour la spécialisation `future<void>` , la méthode retourne **`void`** .

Dans d’autres spécialisations, la méthode déplace sa valeur de retour à partir de la valeur stockée. Par conséquent, n’appelez cette méthode qu’une seule fois.

## <a name="futureoperator"></a><a name="op_eq"></a>futur :: Operator =

Transfère un état asynchrone associé d’un objet spécifié.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Paramètres

*Oui*\
Objet `future`.

### <a name="return-value"></a>Valeur de retour

`*this`

### <a name="remarks"></a>Notes

Après le *transfert, ne possède plus d'* état asynchrone associé.

## <a name="futureshare"></a><a name="share"></a>futur :: partager

Convertit l’objet en un objet [shared_future](../standard-library/shared-future-class.md).

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Valeur de retour

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>futur :: valide

Spécifie si l’objet a un état asynchrone associé.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Valeur de retour

**`true`** Si l’objet a un état asynchrone associé ; Sinon, **`false`** .

## <a name="futurewait"></a><a name="wait"></a>futur :: wait

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Notes

Un état asynchrone associé est *prêt* uniquement si son fournisseur asynchrone a stocké une valeur de retour ou si une exception a été stockée.

## <a name="futurewait_for"></a><a name="wait_for"></a>futur :: wait_for

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou que l’intervalle de temps spécifié soit écoulé.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Paramètres

*Rel_time*\
Objet [chrono::duration](../standard-library/duration-class.md) qui spécifie un intervalle de temps maximal pour le blocage du thread.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est prêt uniquement si son fournisseur asynchrone a stocké une valeur de retour ou une exception.

## <a name="futurewait_until"></a><a name="wait_until"></a>futur :: wait_until

Bloque le thread actuel jusqu’à ce que l’état asynchrone associé soit *prêt* ou jusqu’à un point spécifié dans le temps.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Paramètres

*Abs_time*\
Objet [chrono::time_point](../standard-library/time-point-class.md) qui spécifie un point dans le temps après lequel le thread peut être débloqué.

### <a name="return-value"></a>Valeur de retour

[future_status](../standard-library/future-enums.md#future_status) qui indique la raison du retour.

### <a name="remarks"></a>Notes

Un état asynchrone associé est *prêt* uniquement si son fournisseur asynchrone a stocké une valeur de retour ou si une exception a été stockée.

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
