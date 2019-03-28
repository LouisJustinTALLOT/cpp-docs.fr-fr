---
title: Platform::Collections::BackInsertIterator, classe
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: 02aee3101156b28dbd59ccd51c071e6774ca1e7a
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564721"
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
|[BackInsertIterator::BackInsertIterator](#ctor)|Initialise une nouvelle instance de la classe BackInsertIterator.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[BackInsertIterator::operator*, opérateur](#operator-dereference)|Extrait une référence au BackInsertIterator actif.|
|[BackInsertIterator::operator++, opérateur](#operator-increment)|Retourne une référence au BackInsertIterator actif. L'itérateur est pas modifié.|
|[BackInsertIterator::operator=, opérateur](#operator-assign)|Ajoute l'objet spécifié à la fin de la collection séquentielle en cours.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`BackInsertIterator`

### <a name="requirements"></a>Configuration requise

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

---
## <a name="ctor"></a>  BackInsertIterator::BackInsertIterator Constructor

Initialise une nouvelle instance de la classe `BackInsertIterator`.

## <a name="syntax"></a>Syntaxe

```

explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Paramètres

*v*<br/>
Un IVector\<T > objet.

### <a name="remarks"></a>Notes

Un `BackInsertIterator` insère des éléments après le dernier élément de l'objet spécifié par le paramètre `v`.

## <a name="operator-assign"></a>  BackInsertIterator::operator= Operator

Ajoute l'objet spécifié à la fin de la collection séquentielle en cours.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Paramètres

*t*<br/>
Objet à ajouter à la collection actuelle.

### <a name="return-value"></a>Valeur de retour

Référence au BackInsertIterator actif.

## <a name="operator-dereference"></a>  BackInsertIterator::operator* Operator

Extrait une référence au BackInsertIterator actif.

## <a name="syntax"></a>Syntaxe

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Valeur de retour

Référence au BackInsertIterator actif.

### <a name="remarks"></a>Notes

Cet opérateur retourne une référence au BackInsertIterator actif, et non à un élément dans la collection actuelle.

## <a name="operator-increment"></a>  BackInsertIterator::operator++ Operator

Retourne une référence au BackInsertIterator actif. L'itérateur est pas modifié.

## <a name="syntax"></a>Syntaxe

```

BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Valeur de retour

Référence au BackInsertIterator actif.

### <a name="remarks"></a>Notes

Par conception, le premier exemple de syntaxe préincrémente le BackInsertIterator actuel et la deuxième syntaxe postincrémente le BackInsertIterator actuel. Le type `int` dans la deuxième syntaxe n'indique pas un opérande entier réel mais une post-incrémentation.

Toutefois, cet opérateur ne modifie pas réellement le BackInsertIterator. Au lieu de cela, l'opérateur retourne une référence à l'itérateur actuel non modifié. Il s’agit du même comportement que [opérateur *](#operator-dereference).

## <a name="see-also"></a>Voir aussi

[Plateforme Namespace](platform-namespace-c-cx.md)
