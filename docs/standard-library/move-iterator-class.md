---
title: move_iterator, classe
ms.date: 03/27/2019
f1_keywords:
- iterator/std::move_iterator
- iterator/std::move_iterator::iterator_type
- iterator/std::move_iterator::iterator_category
- iterator/std::move_iterator::value_type
- iterator/std::move_iterator::difference_type
- iterator/std::move_iterator::pointer
- iterator/std::move_iterator::reference
- iterator/std::move_iterator::base
helpviewer_keywords:
- std::move_iterator [C++]
- std::move_iterator [C++], iterator_type
- std::move_iterator [C++], iterator_category
- std::move_iterator [C++], value_type
- std::move_iterator [C++], difference_type
- std::move_iterator [C++], pointer
- std::move_iterator [C++], reference
- std::move_iterator [C++], base
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
ms.openlocfilehash: 3e2e62946325c082e761b6997ae584419175f8fe
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346196"
---
# <a name="moveiterator-class"></a>move_iterator, classe

Le modèle de classe `move_iterator` est un wrapper pour un itérateur. Le move_iterator fournit le même comportement que l'itérateur qu'il encapsule (ou stocke), à la différence près qu'il convertit l'opérateur de déréférence de l'itérateur stocké en une référence rvalue, convertissant ainsi une copie en déplacement. Pour plus d’informations sur les rvalues, consultez [Déclarateur de référence Rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="syntax"></a>Syntaxe

```cpp
class move_iterator;
```

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet qui se comporte comme un itérateur, sauf lorsqu'il est déréférencé. Elle stocke un itérateur d’accès aléatoire de type `Iterator`, accessible par le biais de la fonction membre `base()`. Toutes les opérations effectuées sur un `move_iterator` sont exécutées directement sur l'itérateur stocké, mais le résultat du `operator*` est implicitement converti en `value_type&&` pour créer une référence rvalue.

Un `move_iterator` peut être capable d'effectuer des opérations qui ne sont pas définies par l'itérateur encapsulé. Ces opérations ne doivent pas être utilisées.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[move_iterator](#move_iterator)|Constructeur des objets de type `move_iterator`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[iterator_type](#iterator_type)|Synonyme pour le paramètre du modèle `RandomIterator`.|
|[iterator_category](#iterator_category)|Un synonyme pour une plus longue **typename** expression du même nom, `iterator_category` identifie les fonctionnalités générales de l’itérateur.|
|[value_type](#value_type)|Un synonyme pour une plus longue **typename** expression du même nom, `value_type` décrit le type de l’itérateur sont des éléments.|
|[difference_type](#difference_type)|Un synonyme pour une plus longue **typename** expression du même nom, `difference_type` décrit le type intégral requis aux valeurs d’exprimer des différences entre les éléments.|
|[pointer](#pointer)|Synonyme du paramètre de modèle `RandomIterator`.|
|[reference](#reference)|Synonyme de la référence `rvalue` `value_type&&`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[base](#base)|La fonction membre retourne l'itérateur stocké encapsulé par le `move_iterator`.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[move_iterator::operator*](#op_star)|Retourne `(reference)*base().`.|
|[move_iterator::operator++](#op_add_add)|Incrémente l'itérateur stocké. Le comportement exact varie selon qu'il s'agit d'une préincrémentation ou d'une postincrémentation.|
|[move_iterator::operator--](#operator--)|Décrémente l'itérateur stocké. Le comportement exact varie selon qu'il s'agit d'une préincrémentation ou d'une postincrémentation.|
|[move_iterator::operator-&gt;](#op_arrow)|Retourne `&**this`.|
|[move_iterator::operator-](#operator-)|Retourne `move_iterator(*this) -=` en soustrayant d’abord la valeur située à droite de la position actuelle.|
|[move_iterator::operator[]](#op_at)|Retourne `(reference)*(*this + off)`. Permet de spécifier un décalage depuis la base actuelle pour obtenir la valeur de l'emplacement.|
|[move_iterator::operator+](#op_add)|Retourne la valeur `move_iterator(*this) +=`. Permet d'ajouter un décalage à la base pour obtenir la valeur de l'emplacement.|
|[move_iterator::operator+=](#op_add_eq)|Ajoute la valeur située à droite de l'itérateur stocké, et retourne `*this`.|
|[move_iterator::operator-=](#operator-_eq)|Soustrait la valeur située à droite de l'itérateur stocké, et retourne `*this`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="base"></a>  move_iterator::base

Retourne l'itérateur stocké pour ce `move_iterator`.

```cpp
RandomIterator base() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne l'itérateur stocké.

## <a name="difference_type"></a>  move_iterator::difference_type

Le type `difference_type` est un `typedef` `move_iterator` basé sur la caractéristique d'itérateur `difference_type`. Vous pouvez utiliser indifféremment l'un ou l'autre.

```cpp
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la caractéristique d'itérateur `typename iterator_traits<RandomIterator>::pointer`.

## <a name="iterator_category"></a>  move_iterator::iterator_category

Le type `iterator_category` est un `typedef` `move_iterator` basé sur la caractéristique d'itérateur `iterator_category`. Vous pouvez utiliser indifféremment l'un ou l'autre.

```cpp
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la caractéristique d'itérateur `typename iterator_traits<RandomIterator>::iterator_category`.

## <a name="iterator_type"></a>  move_iterator::iterator_type

Le type `iterator_type` est basé sur le paramètre de modèle `RandomIterator` pour le modèle de classe `move_iterator`. Vous pouvez utiliser indifféremment l'un ou l'autre.

```cpp
typedef RandomIterator iterator_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `RandomIterator`.

## <a name="move_iterator"></a>  move_iterator::move_iterator

Construit un itérateur de déplacement. Utilise le paramètre comme itérateur stocké.

```cpp
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
Itérateur à utiliser comme itérateur stocké.

### <a name="remarks"></a>Notes

Le premier constructeur initialise l'itérateur stocké avec son constructeur par défaut. Les autres constructeurs initialisent l'itérateur stocké avec `base.base()`.

## <a name="op_add_eq"></a>  move_iterator::operator+=

Ajoute un offset à l'itérateur stocké, pour que celui-ci pointe vers l'élément au nouvel emplacement actuel. L'opérateur déplace ensuite le nouvel élément actif.

```cpp
move_iterator& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Paramètres

*_Off*<br/>
Offset à ajouter à la position actuelle pour déterminer la nouvelle position actuelle.

### <a name="return-value"></a>Valeur de retour

Retourne le nouvel élément actif.

### <a name="remarks"></a>Notes

L’opérateur ajoute *_Off* à l’itérateur stocké. Il retourne ensuite `*this`.

## <a name="operator-_eq"></a>  move_iterator::operator-=

Recule du nombre spécifié d'éléments. Cet opérateur soustrait un offset de l'itérateur stocké.

```cpp
move_iterator& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Paramètres

### <a name="remarks"></a>Notes

L'opérateur évalue `*this += -_Off`. Il retourne ensuite `*this`.

## <a name="op_add_add"></a>  move_iterator::operator++

Incrémente l'itérateur stocké qui appartient à ce `move_iterator.`. L'élément actuel est accessible par l'opérateur d'incrémentation. L'élément suivant est accessible par l'opérateur de préincrémentation.

```cpp
move_iterator& operator++();
move_iterator operator++(int);
```

### <a name="parameters"></a>Paramètres

### <a name="remarks"></a>Notes

Le premier opérateur (préincrémentation) incrémente l'itérateur stocké. Il retourne ensuite `*this`.

Le deuxième opérateur (postincrémentation) effectue une copie de `*this` et évalue `++*this`. Ensuite, il retourne la copie.

## <a name="op_add"></a>  move_iterator::operator+

Retourne la position de l'itérateur avancée d'un nombre quelconque d'éléments.

```cpp
move_iterator operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Paramètres

### <a name="remarks"></a>Notes

L’opérateur retourne `move_iterator(*this) +=` `_Off`.

## <a name="op_at"></a>  move_iterator::operator[]

Accorde l'accès à l'index de tableau aux éléments dans toute la plage du `move iterator`.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Paramètres

### <a name="remarks"></a>Notes

L'opérateur retourne `(reference)*(*this + _Off)`.

## <a name="operator--"></a>  move_iterator::operator--

Les opérateurs membres de prédécrémentation et de postdécrémentation effectuent une décrémentation sur l'itérateur stocké.

```cpp
move_iterator& operator--();
move_iterator operator--();
```

### <a name="parameters"></a>Paramètres

### <a name="remarks"></a>Notes

Le premier opérateur membre (prédécrémentation) décrémente l'itérateur stocké. Il retourne ensuite `*this`.

Le deuxième opérateur (postdécrémentation) effectue une copie de `*this` et évalue `--*this`. Ensuite, il retourne la copie.

## <a name="operator-"></a>  move_iterator::operator-

Décrémente l'itérateur stocké et retourne la valeur indiquée.

```cpp
move_iterator operator-(difference_type _Off) const;
```

### <a name="parameters"></a>Paramètres

### <a name="remarks"></a>Notes

L'opérateur retourne `move_iterator(*this) -= _Off`.

## <a name="op_star"></a>  move_iterator::operator*

Déréférence l'itérateur stocké et retourne la valeur. Se comporte comme une `rvalue reference` et exécute une assignation de déplacement. L'opérateur transfère l'élément actuel hors de l'itérateur de base. L'élément qui suit devient le nouvel élément actuel.

```cpp
reference operator*() const;
```

### <a name="remarks"></a>Notes

L'opérateur retourne `(reference)*base()`.

## <a name="op_arrow"></a>  move_iterator::operator-&gt;

Comme un `RandomIterator` `operator->` normal, il fournit un accès aux champs qui appartiennent à l'élément actuel.

```cpp
pointer operator->() const;
```

### <a name="remarks"></a>Notes

L'opérateur retourne `&**this`.

## <a name="pointer"></a>  move_iterator::pointer

Le type `pointer` est un **typedef** en fonction de l’itérateur aléatoire `RandomIterator` pour `move_iterator`et peuvent être utilisées indifféremment.

```cpp
typedef RandomIterator  pointer;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `RandomIterator`.

## <a name="reference"></a>  move_iterator::reference

Le type `reference` est un **typedef** selon `value_type&&` pour `move_iterator`et peuvent être utilisées indifféremment avec `value_type&&`.

```cpp
typedef value_type&& reference;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `value_type&&`, qui est une référence rvalue.

## <a name="value_type"></a>  move_iterator::value_type

Le type `value_type` est un `typedef` `move_iterator` basé sur la caractéristique d'itérateur `value_type`. Vous pouvez utiliser indifféremment l'un ou l'autre.

```cpp
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de la caractéristique d'itérateur `typename iterator_traits<RandomIterator>::value_type`.

## <a name="see-also"></a>Voir aussi

[\<iterator>](../standard-library/iterator.md)<br/>
[Lvalues et Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[Constructeurs de déplacement et opérateurs d’assignation de déplacement (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
