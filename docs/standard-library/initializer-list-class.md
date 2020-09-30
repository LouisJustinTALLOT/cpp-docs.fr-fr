---
title: initializer_list, classe
description: Référence pour la classe initializer_list dans la bibliothèque standard C++, telle qu’elle est implémentée par Microsoft dans Visual Studio.
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: 232855fbcac1e4df9af7cf956fda80201326a401
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504632"
---
# <a name="initializer_list-class"></a>initializer_list, classe

Fournit l'accès à un tableau d'éléments dans lequel chaque membre est du type spécifié.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>Paramètres

*Entrer*\
Type de données d'élément à stocker dans le `initializer_list`.

## <a name="remarks"></a>Remarques

Un `initializer_list` peut être construit à l'aide d'une liste d'initialiseurs entre accolades :

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

Le compilateur transforme les listes d'initialiseurs entre accolades avec des éléments homogènes en un `initializer_list` chaque fois que la signature de fonction nécessite un `initializer_list`. Pour plus d’informations sur l’utilisation de `initializer_list` , consultez [constructeurs d’initialisation uniforme et de délégation](../cpp/initializing-classes-and-structs-without-constructors-cpp.md)

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[initializer_list](#initializer_list)|Construit un objet de type `initializer_list`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|`value_type`|Type des éléments dans le `initializer_list`.|
|`reference`|Type qui fournit une référence à un élément stocké dans le `initializer_list`.|
|`const_reference`|Type qui fournit une référence constante à un élément dans le `initializer_list`.|
|`size_type`|Type qui représente le nombre d'éléments dans le `initializer_list`.|
|`iterator`|Type qui fournit un itérateur pour le `initializer_list`.|
|`const_iterator`|Type qui fournit un itérateur constant pour le `initializer_list`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[commencer](#begin)|Retourne un pointeur vers le premier élément d'une `initializer_list`.|
|[end](#end)|Retourne un pointeur vers la position au-delà du dernier élément dans un `initializer_list`.|
|[size](#size)|Retourne le nombre d'éléments d'un `initializer_list`.|

## <a name="requirements"></a>Configuration requise

**En-tête :**\<initializer_list>

**Espace de noms :** std

## <a name="initializer_listbegin"></a><a name="begin"></a> initializer_list :: Begin

Retourne un pointeur vers le premier élément d'une `initializer_list`.

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le premier élément de la `initializer_list`. Si la liste est vide, le pointeur est le même pour le début et pour la fin de la liste.

## <a name="initializer_listend"></a><a name="end"></a> initializer_list :: fin

Retourne un pointeur vers la position au-delà du dernier élément dans un `initializer list`.

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers la position au-delà du dernier élément de la liste. Si la liste est vide, elle est identique au pointeur vers le premier élément de la liste.

## <a name="initializer_listinitializer_list"></a><a name="initializer_list"></a> initializer_list :: initializer_list

Construit un objet de type `initializer_list`.

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>Paramètres

*Premier*\
Position du premier élément de la plage d'éléments à copier.

*Famille*\
Position du premier élément au-delà de la plage d'éléments à copier.

### <a name="remarks"></a>Remarques

Une `initializer_list` est basée sur un tableau d'objets du type spécifié. La copie d’une `initializer_list` crée une deuxième instance d’une liste pointant vers les mêmes objets ; les objets sous-jacents ne sont pas copiés.

### <a name="example"></a>Exemple

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="initializer_listsize"></a><a name="size"></a> initializer_list :: Size

Retourne le nombre d'éléments figurant dans la liste.

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>Valeur renvoyée

Nombre d'éléments dans la liste.

## <a name="see-also"></a>Voir aussi

[<forward_list>](../standard-library/forward-list.md)
