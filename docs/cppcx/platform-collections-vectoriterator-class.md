---
title: Platform::Collections::VectorIterator, classe
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorIterator::VectorIterator
helpviewer_keywords:
- VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
ms.openlocfilehash: bade67a104774c3ab6187e250c6faf6969002c0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218414"
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator, classe

Fournit un itérateur de bibliothèque STL (Standard Template Library) pour les objets dérivés de l’interface Windows Runtime IVector.

VectorIterator est un itérateur de proxy qui stocke des éléments de type VectorProxy \<T> . Toutefois, l'objet proxy n'est presque jamais visible par le code utilisateur. Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class VectorIterator;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Nom de type de la classe de modèle VectorIterator.

### <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`difference_type`|Différence de pointeur (ptrdiff_t).|
|`iterator_category`|Catégorie d'un itérateur à accès aléatoire (::std::random_access_iterator_tag).|
|`pointer`|Pointeur vers un type interne, Platform :: Collections ::D étails :: VectorProxy \<T> , qui est requis pour l’implémentation de VectorIterator.|
|`reference`|Référence à un type interne, Platform :: Collections ::D étails :: VectorProxy \<T> ,, qui est requis pour l’implémentation de VectorIterator.|
|`value_type`|Nom de type `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[VectorIterator :: VectorIterator](#ctor)|Initialise une nouvelle instance de la classe VectorIterator.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[VectorIterator :: Operator-, opérateur](#operator-minus)|Soustrait un nombre spécifié d'éléments de l'itérateur actuel en cédant un nouvel itérateur, ou un itérateur spécifié de l'itérateur actuel en cédant le nombre d'éléments entre les itérateurs.|
|[VectorIterator :: Operator--, opérateur](#operator-decrement)|Décrémente le VectorIterator actif.|
|[VectorIterator :: Operator ! =, opérateur](#operator-inequality)|Indique si le VectorIterator actif n'est pas égal à un VectorIterator spécifié.|
|[VectorIterator :: Operator *, opérateur](#operator-dereference)|Récupère une référence à l'élément spécifié par le VectorIterator actif.|
|[VectorIterator ::, opérateur\[\]](#operator-at)|Récupère une référence à l'élément qui est un décalage spécifié à partir de l'objet VectorIterator actuel.|
|[VectorIterator :: Operator +, opérateur](#operator-plus)|Retourne un VectorIterator qui référence l'élément spécifié au décalage spécifié à partir du VectorIterator spécifié.|
|[VectorIterator :: Operator + +, opérateur](#operator-increment)|Incrémente le VectorIterator actif.|
|[VectorIterator :: Operator + =, opérateur](#operator-plus-assign)|Incrémente le VectorIterator actif du décalage spécifié.|
|[VectorIterator :: Operator<, opérateur](#operator-less-than)|Indique si le VectorIterator actuel est inférieur au VectorIterator spécifié.|
|[VectorIterator :: Operator \< =, opérateur](#operator-less-than-or-equals)|Indique si l'objet VectorIterator actuel est inférieur ou égal à un objet VectorIterator spécifié.|
|[VectorIterator::operator-=, opérateur](#operator-minus-equals)|Décrémente l'objet VectorIterator actuel du décalage spécifié.|
|[VectorIterator :: Operator = =, opérateur](#operator-equality)|Indique si l'objet VectorIterator actuel est égal à un objet VectorIterator spécifié.|
|[VectorIterator :: Operator>, opérateur](#operator-greater-than)|Indique si le VectorIterator actif est supérieur au VectorIterator spécifié.|
|[VectorIterator :: operator-opérateur->](#operator-arrow)|Récupère l'adresse de l'élément référencé par le VectorIterator actif.|
|[VectorIterator :: Operator>=, opérateur](#operator-greater-than-or-equals)|Indique si le VectorIterator actif est supérieur ou égal à un VectorIterator spécifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VectorIterator`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="vectoriteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorIterator :: Operator-, &gt; opérateur

Récupère l'adresse de l'élément référencé par le VectorIterator actif.

### <a name="syntax"></a>Syntaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément référencé par le VectorIterator actif.

Le type de la valeur de retour est un type interne non spécifié nécessaire pour l’implémentation de cet opérateur.

## <a name="vectoriteratoroperator---operator"></a><a name="operator-decrement"></a>VectorIterator :: Operator--, opérateur

Décrémente le VectorIterator actif.

### <a name="syntax"></a>Syntaxe

```

VectorIterator& operator--();
VectorIterator operator--(int);
```

### <a name="return-value"></a>Valeur de retour

La première syntaxe décrémente le VectorIterator actif puis le retourne. La deuxième syntaxe retourne une copie du VectorIterator actif puis décrémente le VectorIterator actif.

### <a name="remarks"></a>Notes

La première syntaxe VectorIterator prédécrémente le VectorIterator actif.

La deuxième syntaxe post-décrémente le VectorIterator actif. Le **`int`** type dans la deuxième syntaxe indique une opération de post-décrémentation, et non un opérande entier réel.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-dereference"></a>VectorIterator :: Operator, \* opérateur

Récupère l’adresse de l’élément spécifié par le VectorIterator actif.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Valeur de retour

Élément spécifié par le VectorIterator actif.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-equality"></a>VectorIterator :: Operator = =, opérateur

Indique si l'objet VectorIterator actuel est égal à un objet VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator==(const VectorIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le VectorIterator actuel est égal à *other*; Sinon, **`false`** .

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorIterator :: Operator, &gt; opérateur

Indique si le VectorIterator actif est supérieur au VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator>(const VectorIterator& other) const
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le VectorIterator actuel est supérieur à *other*; Sinon, **`false`** .

## <a name="vectoriteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorIterator :: Operator &gt; =, opérateur

Indique si le VectorIterator actif est supérieur ou égal au VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator>=(const VectorIterator& other) const
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le VectorIterator actuel est supérieur ou égal à *other*; Sinon, **`false`** .

## <a name="vectoriteratoroperator-operator"></a><a name="operator-increment"></a>VectorIterator :: Operator + +, opérateur

Incrémente le VectorIterator actif.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator++();
VectorIterator operator++(int);
```

### <a name="return-value"></a>Valeur de retour

La première syntaxe incrémente le VectorIterator actif puis le retourne. La deuxième syntaxe retourne une copie du VectorIterator actif puis incrémente le VectorIterator actif.

### <a name="remarks"></a>Notes

La première syntaxe VectorIterator préincrémente le VectorIterator actif.

La deuxième syntaxe postincrémente le VectorIterator actif. Le **`int`** type dans la deuxième syntaxe indique une opération postérieure à l’incrémentation, et non un opérande entier réel.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-inequality"></a>VectorIterator :: Operator ! =, opérateur

Indique si le VectorIterator actif n'est pas égal à un VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const VectorIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le VectorIterator actuel n’est pas égal à *other*; Sinon, **`false`** .

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorIterator :: Operator, &lt; opérateur

Indique si le VectorIterator actuel est inférieur au VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator<(const VectorIterator& other) const
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le VectorIterator actuel est inférieur à *other*; Sinon, **`false`** .

## <a name="vectoriteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorIterator :: Operator &lt; =, opérateur

Indique si l'objet VectorIterator actuel est inférieur ou égal à un objet VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator<=(const VectorIterator& other) const
```

### <a name="parameters"></a>Paramètres

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

**`true`** Si le VectorIterator actuel est inférieur ou égal à *other*; Sinon, **`false`** .

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus"></a>VectorIterator :: Operator-, opérateur

Soustrait un nombre spécifié d'éléments de l'itérateur actuel en cédant un nouvel itérateur, ou un itérateur spécifié de l'itérateur actuel en cédant le nombre d'éléments entre les itérateurs.

### <a name="syntax"></a>Syntaxe

```

VectorIterator operator-(difference_type n) const;

difference_type operator-(const VectorIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Nombre d'éléments.

*autres*<br/>
Autre objet VectorIterator.

### <a name="return-value"></a>Valeur de retour

La première syntaxe d’opérateur retourne un objet VectorIterator qui a `n` éléments en moins que l’objet VectorIterator actif. La deuxième syntaxe d’opérateur retourne le nombre d’éléments entre l’objet actif et l’objet VectorIterator `other`.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus-assign"></a>VectorIterator :: Operator + =, opérateur

Incrémente le VectorIterator actif du décalage spécifié.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Déplacement d'un entier.

### <a name="return-value"></a>Valeur de retour

Objet VectorIterator mis à jour.

## <a name="vectoriteratoroperator-operator"></a><a name="operator-plus"></a>VectorIterator :: Operator +, opérateur

Retourne un VectorIterator qui référence l'élément spécifié au décalage spécifié à partir du VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```

VectorIterator operator+(difference_type n);

template <typename T>
inline VectorIterator<T> operator+(
  ptrdiff_t n,
  const VectorIterator<T>& i);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Dans la deuxième syntaxe, typename du VectorIterator.

*n*<br/>
Déplacement d'un entier.

*i*<br/>
Dans la deuxième syntaxe, un VectorIterator.

### <a name="return-value"></a>Valeur de retour

Dans la première syntaxe, VectorIterator qui référence l'élément spécifié au décalage spécifié à partir du VectorIterator actuel.

Dans la deuxième syntaxe, VectorIterator qui référence l'élément au décalage spécifié à partir du début du paramètre `i`.

### <a name="remarks"></a>Notes

Exemple pour la première syntaxe

## <a name="vectoriteratoroperator--operator"></a><a name="operator-minus-equals"></a>VectorIterator :: Operator-=, opérateur

Décrémente l'objet VectorIterator actuel du décalage spécifié.

### <a name="syntax"></a>Syntaxe

```
VectorIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Déplacement d'un entier.

### <a name="return-value"></a>Valeur de retour

Objet VectorIterator mis à jour.

## <a name="vectoriteratoroperator"></a><a name="operator-at"></a>VectorIterator ::, opérateur\[\]

Récupère une référence à l'élément qui est un décalage spécifié à partir de l'objet VectorIterator actuel.

### <a name="syntax"></a>Syntaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Déplacement d'un entier.

### <a name="return-value"></a>Valeur de retour

Élément qui est décalé par les éléments `n` à partir du VectorIterator actif.

## <a name="vectoriteratorvectoriterator-constructor"></a><a name="ctor"></a>VectorIterator :: VectorIterator, constructeur

Initialise une nouvelle instance de la classe VectorIterator.

### <a name="syntax"></a>Syntaxe

```
VectorIterator();

explicit VectorIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

### <a name="parameters"></a>Paramètres

*v*<br/>
Objet IVector \<T> .

### <a name="remarks"></a>Notes

Le premier exemple de syntaxe est le constructeur par défaut. Le deuxième exemple de syntaxe est un constructeur explicite qui est utilisé pour construire un VectorIterator à partir d’un \<T> objet IVector.

## <a name="see-also"></a>Voir aussi

[Espace de noms de plateforme](platform-namespace-c-cx.md)
