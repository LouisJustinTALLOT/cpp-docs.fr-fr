---
description: 'En savoir plus sur : classe Platform :: Collections :: BackInsertIterator'
title: Platform::Collections::BackInsertIterator, classe
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: d4130db388470b5e29b545b66b06ee85b2cbb608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283990"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator, classe

Représente un itérateur qui ne remplace pas les éléments mais les insère dans le back end d'une collection séquentielle.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type d'élément de la collection active.

### <a name="remarks"></a>Notes

La classe BackInsertIterator implémente les règles requises par la [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[BackInsertIterator :: BackInsertIterator](#ctor)|Initialise une nouvelle instance de la classe BackInsertIterator.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[BackInsertIterator :: Operator *, opérateur](#operator-dereference)|Extrait une référence au BackInsertIterator actif.|
|[BackInsertIterator :: Operator + +, opérateur](#operator-increment)|Retourne une référence au BackInsertIterator actif. L'itérateur est pas modifié.|
|[BackInsertIterator::operator=, opérateur](#operator-assign)|Ajoute l'objet spécifié à la fin de la collection séquentielle en cours.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BackInsertIterator`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a> BackInsertIterator :: BackInsertIterator, constructeur

Initialise une nouvelle instance de la classe `BackInsertIterator`.

### <a name="syntax"></a>Syntaxe

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Paramètres

*v*<br/>
Objet IVector \<T> .

### <a name="remarks"></a>Notes

Un `BackInsertIterator` insère des éléments après le dernier élément de l'objet spécifié par le paramètre `v`.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a> BackInsertIterator :: Operator =, opérateur

Ajoute l'objet spécifié à la fin de la collection séquentielle en cours.

### <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Paramètres

*t*<br/>
Objet à ajouter à la collection actuelle.

### <a name="return-value"></a>Valeur renvoyée

Référence au BackInsertIterator actif.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a> BackInsertIterator :: Operator *, opérateur

Extrait une référence au BackInsertIterator actif.

### <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Valeur de retour

Référence au BackInsertIterator actif.

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence au BackInsertIterator actif, et non à un élément dans la collection actuelle.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a> BackInsertIterator :: Operator + +, opérateur

Retourne une référence au BackInsertIterator actif. L'itérateur est pas modifié.

### <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Valeur de retour

Référence au BackInsertIterator actif.

### <a name="remarks"></a>Notes

Par conception, le premier exemple de syntaxe préincrémente le BackInsertIterator actuel et la deuxième syntaxe postincrémente le BackInsertIterator actuel. Le **`int`** type dans la deuxième syntaxe indique une opération postérieure à l’incrémentation, et non un opérande entier réel.

Toutefois, cet opérateur ne modifie pas réellement le BackInsertIterator. Au lieu de cela, l'opérateur retourne une référence à l'itérateur actuel non modifié. Il s’agit du même comportement que l' [opérateur *](#operator-dereference).

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)
