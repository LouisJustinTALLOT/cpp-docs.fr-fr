---
title: Platform::Collections::InputIterator, classe
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354563"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator, classe

Fournit un inputiterator de bibliothèque standard de modèle pour des collections dérivées du Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Paramètres

*X*<br/>
Nom de type de la classe de modèle InputIterator.

### <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`difference_type`|Différence de pointeur (ptrdiff_t).|
|`iterator_category`|Catégorie d’un itérateur d’entrée (:: std::input_iterator_tag).|
|`pointer`|Pointeur vers un `const X`|
|`reference`|Référence à un `const X`|
|`value_type`|Nom de type `X` .|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|Initialise une nouvelle instance de la classe InputIterator.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[InputIterator::opérateur!](#operator-inequality)|Indique si l'InputIterator actif n'est pas égal à un InputIterator spécifié.|
|[InputIterator::operator*, opérateur](#operator-dereference)|Récupère une référence à l’élément spécifié par l’InputIterator actif.|
|[InputIterator::opérateur OPÉRATEUR](#operator-increment)|Incrémente l'objet InputIterator actuel.|
|[InputIterator::opérateur OPÉRATEUR](#operator-equality)|Indique si l'InputIterator actif est égal à un InputIterator spécifié.|
|[InputIterator::opérateur-> opérateur](#operator-arrow)|Récupère l’adresse de l’élément référencé par l’InputIterator actif.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`InputIterator`

### <a name="requirements"></a>Spécifications

**En-tête :** collection.h

**Espace de noms :** Platform::Collections

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator::InputIterator Constructor

Initialise une nouvelle instance de la classe InputIterator.

### <a name="syntax"></a>Syntaxe

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Paramètres

*Itérateur*<br/>
Objet itérateur.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator::opérateur-&gt; Opérateur

Récupère l’adresse de l’élément spécifié par l’objet InputIterator actif.

### <a name="syntax"></a>Syntaxe

```
pointer operator->() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse de l’élément spécifié par l’objet InputIterator actif.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator::opérateur\*

Récupère une référence à l’élément spécifié par l’InputIterator actif.

### <a name="syntax"></a>Syntaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Valeur de retour

Élément spécifié par l’InputIterator actif.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator::opérateur OPÉRATEUR

Indique si l'InputIterator actif est égal à un InputIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Autre InputIterator.

### <a name="return-value"></a>Valeur de retour

**vrai** si l’InputIterator actuel est égal à *d’autres*; autrement, **faux**.

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator::opérateur OPÉRATEUR

Incrémente l'objet InputIterator actuel.

### <a name="syntax"></a>Syntaxe

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Valeur de retour

La première syntaxe incrémente l'objet InputIterator actuel puis le retourne. La deuxième syntaxe retourne une copie de l'objet InputIterator actuel, puis incrémente l'objet InputIterator actuel.

### <a name="remarks"></a>Notes

La première syntaxe InputIterator préincrémente l'objet InputIterator actuel.

La deuxième syntaxe postincrémente l'objet InputIterator actuel. Le type `int` dans la deuxième syntaxe n'indique pas un opérande entier réel mais une post-incrémentation.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator::opérateur!

Indique si l'InputIterator actif n'est pas égal à un InputIterator spécifié.

### <a name="syntax"></a>Syntaxe

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Paramètres

*Autres*<br/>
Autre InputIterator.

### <a name="return-value"></a>Valeur de retour

**vrai** si l’InputIterator actuel n’est pas égal à *d’autres*; autrement, **faux**.

## <a name="see-also"></a>Voir aussi

[Espace nom de la plate-forme](platform-namespace-c-cx.md)
