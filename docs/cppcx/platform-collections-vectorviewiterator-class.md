---
title: Platform::Collections::VectorViewIterator, classe
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 01ae4286e996db9819cb697360f6de9c344edd21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363699"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Platform::Collections::VectorViewIterator, classe

Fournit un itérateur standard de bibliothèque de`IVectorView` modèle pour les objets dérivés de l’interface Windows Runtime.

`ViewVectorIterator` est un itérateur de proxy qui stocke des éléments de type `VectorProxy<T>`. Toutefois, l'objet proxy n'est presque jamais visible par le code utilisateur. Pour plus d'informations, consultez [Collections (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Typename de la classe de modèle VectorViewIterator.

### <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`difference_type`|Différence de pointeur (ptrdiff_t).|
|`iterator_category`|Catégorie d'un itérateur à accès aléatoire (::std::random_access_iterator_tag).|
|`pointer`|Pointeur vers un type interne requis pour l'implémentation de VectorViewIterator.|
|`reference`|Référence à un type interne requis pour l'implémentation de VectorViewIterator.|
|`value_type`|Nom de type `T` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Initialise une nouvelle instance de la classe VectorViewIterator.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[VectorViewIterator::opérateur- Opérateur](#operator-minus)|Soustrait un nombre spécifié d'éléments de l'itérateur actuel en cédant un nouvel itérateur, ou un itérateur spécifié de l'itérateur actuel en cédant le nombre d'éléments entre les itérateurs.|
|[VectorViewIterator::opérateur-- Opérateur](#operator-decrement)|Décrémente le VectorViewIterator actif.|
|[VectorViewIterator::opérateur!](#operator-inequality)|Indique si le VectorViewIterator actuel n'est pas égal à un VectorViewIterator spécifié.|
|[VectorViewIterator::opérateur OPÉRATEUR](#operator-dereference)|Récupère une référence à l'élément spécifié par le VectorViewIterator actif.|
|[VectorViewIterator::opérateur\[\]](#operator-at)|Extrait une référence à l'élément qui est un offset spécifié de l'objet VectorViewIterator actuel.|
|[VectorViewIterator::opérateur OPÉRATEUR](#operator-plus)|Retourne un VectorIterator qui référence l'élément au décalage spécifié à partir du VectorViewIterator spécifié.|
|[VectorViewIterator::opérateur OPÉRATEUR](#operator-increment)|Incrémente l'objet VectorViewIterator actuel.|
|[VectorViewIterator::opérateur OPÉRATEUR](#operator-plus-equals)|Incrémente le VectorViewIterator actuel par le décalage spécifié.|
|[VectorViewIterator::opérateur< opérateur](#operator-less-than)|Indique si le VectorViewIterator actif est inférieur à un VectorViewIterator spécifié.|
|[VectorViewIterator::opérateur\<et opérateur](#operator-less-than-or-equals)|Indique si le VectorViewIterator actif est inférieur ou égal à un VectorViewIterator spécifié.|
|[VectorViewIterator::opérateur-opérateur](#operator-minus-assign)|Décrémente le VectorViewIterator actif du décalage spécifié.|
|[VectorViewIterator::opérateur OPÉRATEUR](#operator-equality)|Indique si le VectorViewIterator actif est égal à un VectorViewIterator spécifié.|
|[VectorViewIterator::opérateur> opérateur](#operator-greater-than)|Indique si le VectorViewIterator actif est supérieur à un VectorViewIterator spécifié.|
|[VectorViewIterator::operator->, opérateur](#operator-arrow)|Récupère l'adresse de l'élément référencé par le VectorViewIterator actif.|
|[VectorViewIterator::opérateur>- Opérateur](#operator-greater-than-or-equals)|Indique si le VectorViewIterator actif est supérieur ou égal à un VectorViewIterator spécifié.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`VectorViewIterator`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="vectorviewiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>VectorViewIterator::opérateur-&gt; Opérateur

Récupère l'adresse de l'élément référencé par le VectorViewIterator actif.

### <a name="syntax"></a>Syntaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Valeur de l’élément référencé par le VectorViewIterator actif.

Le type de la valeur de retour est un type interne non spécifié nécessaire pour l’implémentation de cet opérateur.

## <a name="vectorviewiteratoroperator---operator"></a><a name="operator-decrement"></a>VectorViewIterator::opérateur-- Opérateur

Décrémente le VectorViewIterator actif.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Valeur de retour

La première syntaxe décrémente l’objet VectorViewIterator actif, puis le retourne. La deuxième syntaxe retourne une copie de l’objet VectorViewIterator actif, puis le décrémente.

### <a name="remarks"></a>Notes

La première syntaxe VectorViewIterator prédécrémente l’objet VectorViewIterator actif.

La deuxième syntaxe postdécrémente l’objet VectorViewIterator actif. Le type `int` dans la deuxième syntaxe n’indique pas un opérande entier réel mais une post-décrémentation.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-dereference"></a>VectorViewIterator::opérateur\* opérateur

Récupère une référence à l'élément spécifié par le VectorViewIterator actif.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Valeur de retour

Élément spécifié par le VectorViewIterator actif.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-equality"></a>VectorViewIterator::opérateur OPÉRATEUR

Indique si le VectorViewIterator actif est égal à un VectorViewIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Un autre VectorViewIterator.

### <a name="return-value"></a>Valeur de retour

**vrai** si `VectorViewIterator` le courant est égal à *d’autres*; autrement, **faux**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than"></a>VectorViewIterator::opérateur&gt; opérateur

Indique si le VectorViewIterator actif est supérieur à un VectorViewIterator spécifié.

### <a name="syntax"></a>Syntaxe

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Un autre VectorViewIterator.

### <a name="return-value"></a>Valeur de retour

**vrai** si l’actuel VectorViewIterator est plus grand que *d’autres*; autrement, **faux**.

## <a name="vectorviewiteratoroperatorgt-operator"></a><a name="operator-greater-than-or-equals"></a>VectorViewIterator::opérateur&gt;et opérateur

Indique si `VectorViewIterator` le courant est supérieur `VectorViewIterator`ou égal à celui spécifié .

### <a name="syntax"></a>Syntaxe

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Un autre VectorViewIterator.

### <a name="return-value"></a>Valeur de retour

**vrai** si `VectorViewIterator` le courant est supérieur ou égal à *celui des autres;* autrement, **faux**.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-increment"></a>VectorViewIterator::opérateur OPÉRATEUR

Incrémente l'objet VectorViewIterator actuel.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Valeur de retour

La première syntaxe incrémente l'objet VectorViewIterator actuel, puis le retourne. La deuxième syntaxe retourne une copie de l'objet VectorViewIterator actuel, puis l'incrémente.

### <a name="remarks"></a>Notes

La première syntaxe VectorViewIterator préincrémente l'objet VectorViewIterator actuel.

La deuxième syntaxe postincrémente l'objet VectorViewIterator actuel. Le type `int` dans la deuxième syntaxe n'indique pas un opérande entier réel mais une post-incrémentation.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-inequality"></a>VectorViewIterator::opérateur!

Indique si le VectorViewIterator actuel n'est pas égal à un VectorViewIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Un autre VectorViewIterator.

### <a name="return-value"></a>Valeur de retour

**vrai** si `VectorViewIterator` le courant n’est pas égal à *d’autres*; autrement, **faux**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than"></a>VectorViewIterator::opérateur&lt; opérateur

Indique si le VectorIterator actuel est inférieur au VectorIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Autre `VectorIterator`.

### <a name="return-value"></a>Valeur de retour

**vrai** si `VectorIterator` le courant est inférieur *à d’autres*; autrement, **faux**.

## <a name="vectorviewiteratoroperatorlt-operator"></a><a name="operator-less-than-or-equals"></a>VectorViewIterator::opérateur&lt;et opérateur

Indique si `VectorIterator` le courant est inférieur ou `VectorIterator`égal à un spécifié .

### <a name="syntax"></a>Syntaxe

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Autre `VectorIterator`.

### <a name="return-value"></a>Valeur de retour

**vrai** si `VectorIterator` le courant est inférieur ou égal à *d’autres*; autrement, **faux**.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus"></a>VectorViewIterator::opérateur- Opérateur

Soustrait un nombre spécifié d'éléments de l'itérateur actuel en cédant un nouvel itérateur, ou un itérateur spécifié de l'itérateur actuel en cédant le nombre d'éléments entre les itérateurs.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Nombre d'éléments.

*Autres*<br/>
Un autre VectorViewIterator.

### <a name="return-value"></a>Valeur de retour

La première syntaxe d'opérateur retourne un objet VectorViewIterator qui a un nombre inférieur d'éléments `n` par rapport à l'objet VectorViewIterator actuel. La deuxième syntaxe d'opérateur retourne le nombre d'éléments entre l'objet actuel et l'objet VectorViewIterator `other`.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus-equals"></a>VectorViewIterator::opérateur OPÉRATEUR

Incrémente le VectorViewIterator actuel par le décalage spécifié.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Déplacement d'un entier.

### <a name="return-value"></a>Valeur de retour

VectorViewIterator mis à jour.

## <a name="vectorviewiteratoroperator-operator"></a><a name="operator-plus"></a>VectorViewIterator::opérateur OPÉRATEUR

Retourne un VectorIterator qui référence l'élément au décalage spécifié à partir du VectorViewIterator spécifié.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Dans la deuxième syntaxe, typename du VectorViewIterator.

*n*<br/>
Déplacement d'un entier.

*Ⅰ*<br/>
Dans la deuxième syntaxe, un VectorViewIterator.

### <a name="return-value"></a>Valeur de retour

Dans la première syntaxe, VectorViewIterator qui fait référence à l’élément spécifié au décalage spécifié par rapport au VectorViewIterator actuel.

Dans la deuxième syntaxe, VectorViewIterator qui fait référence à l’élément au décalage spécifié par rapport au début du paramètre `i`.

## <a name="vectorviewiteratoroperator--operator"></a><a name="operator-minus-assign"></a>VectorViewIterator::opérateur-opérateur

Décrémente l'objet VectorIterator actuel du décalage spécifié.

### <a name="syntax"></a>Syntaxe

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Déplacement d'un entier.

### <a name="return-value"></a>Valeur de retour

Objet VectorIterator mis à jour.

## <a name="vectorviewiteratoroperator"></a><a name="operator-at"></a>VectorViewIterator::opérateur\[\]

Extrait une référence à l'élément qui est un offset spécifié de l'objet VectorViewIterator actuel.

### <a name="syntax"></a>Syntaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Paramètres

*n*<br/>
Déplacement d'un entier.

### <a name="return-value"></a>Valeur de retour

Élément qui est déplacé par les éléments `n` de l'objet VectorViewIterator actuel.

## <a name="vectorviewiteratorvectorviewiterator-constructor"></a><a name="ctor"></a>VectorViewIterator::VectorViewIterator Constructor

Initialise une nouvelle instance de la classe VectorViewIterator.

### <a name="syntax"></a>Syntaxe

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Paramètres

*C*<br/>
Un objet IVectorView\<T>.

### <a name="remarks"></a>Notes

Le premier exemple de syntaxe est le constructeur par défaut. Le deuxième exemple de syntaxe est un constructeur explicite qui est utilisé\<pour construire un VectorViewIterator à partir d’un objet IVectorView T>.

## <a name="see-also"></a>Voir aussi

[Espace nom de la plate-forme](platform-namespace-c-cx.md)
