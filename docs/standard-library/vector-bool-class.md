---
title: vector&lt;bool&gt;, classe
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: d4ae53f9a14f04d5656a13c32e75494688c5cdd0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452267"
---
# <a name="vectorltboolgt-class"></a>vector&lt;bool&gt;, classe

La `vector<bool>` classe est une spécialisation partielle de [Vector](../standard-library/vector-class.md) pour les éléments de type **bool**. Il possède un allocateur pour le type sous-jacent utilisé par la spécialisation, qui permet l’optimisation de l’espace en stockant une valeur **bool** par bit.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Notes

Le comportement de cette spécialisation de modèle de classe est identique à celui de vector, à l’exception de quelques différences expliquées dans cet article.

Les opérations qui gèrent le type **bool** correspondent aux valeurs dans le stockage de conteneur. `allocator_traits::construct` n'est pas utilisé pour créer ces valeurs.

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[const_pointer](#const_pointer)|Typedef d'un `const_iterator` qui peut servir de pointeur constant à un élément booléen du `vector<bool>`.|
|[const_reference](#const_reference)|Typedef pour **bool**. Après l'initialisation, il n'applique pas les mises à jour de la valeur d'origine.|
|[pointer](#pointer)|Typedef d'un `iterator` qui peut servir de pointeur à un élément booléen du `vector<bool>`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[flip](#flip)|Inverse tous les bits du `vector<bool>`.|
|[swap](#swap)|Échange les éléments de deux `vector<bool>`.|
|[operator&#91;&#93;](#op_at)|Retourne une référence simulée à l'élément `vector<bool>` à un emplacement spécifié.|
|`at`|Fonctionne comme la fonction non spécialisée [vector](../standard-library/vector-class.md)::at, à la différence près qu’elle utilise la classe proxy [vector\<bool>::reference](#reference_class). Consultez également [operator&#91;&#93;](#op_at).|
|`front`|Fonctionne comme la fonction non spécialisée [vector](../standard-library/vector-class.md)::front, à la différence près qu’elle utilise la classe proxy [vector\<bool>::reference](#reference_class). Consultez également [operator&#91;&#93;](#op_at).|
|`back`|Fonctionne comme la fonction non spécialisée [vector](../standard-library/vector-class.md)::back, à la différence près qu’elle utilise la classe proxy [vector\<bool>::reference](#reference_class). Consultez également [operator&#91;&#93;](#op_at).|

### <a name="proxy-class"></a>Classe proxy

|||
|-|-|
|[vector\<bool>, classe de référence](#reference_class)|Classe qui sert de proxy pour simuler le comportement `bool&`, et dont les objets peuvent fournir des références aux éléments (bits uniques) au sein d'un objet `vector<bool>`.|

## <a name="requirements"></a>Configuration requise

**En-tête** : \<vector>

**Espace de noms :** std

## <a name="const_pointer"></a>  vector\<bool>::const_pointer

Type qui décrit un objet pouvant servir de pointeur de constante vers un élément booléen de la séquence contenue dans l'objet `vector<bool>`.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>  vector\<bool>::const_reference

Type qui décrit un objet pouvant servir de référence de constante à un élément booléen de la séquence contenue dans l'objet `vector<bool>`.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Notes

Pour plus d’informations et des exemples de code, consultez [vector&lt;bool&gt;::reference::operator=](#reference_operator_eq).

## <a name="flip"></a>  vector\<bool>::flip

Inverse tous les bits d'un `vector<bool>`.

```cpp
void flip();
```

### <a name="example"></a>Exemple

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="op_at"></a>  vector\<bool>::operator[]

Retourne une référence simulée à l'élément `vector<bool>` à un emplacement spécifié.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|-|-|
|*Imprim*|Position de l'élément `vector<bool>`.|

### <a name="return-value"></a>Valeur de retour

Objet [vector\<bool>::reference](#reference_class) ou [vector\<bool>::const_reference](#const_reference) qui contient la valeur de l’élément indexé.

Si la position spécifiée est supérieure ou égale à la taille du conteneur, le résultat est non défini.

### <a name="remarks"></a>Notes

Si vous compilez avec _ITERATOR_DEBUG_LEVEL défini, une erreur d’exécution se produit si vous tentez d’accéder à un élément en dehors des limites du vecteur.  Pour plus d'informations, consultez [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Exemple

Cet exemple de code illustre une utilisation correcte de `vector<bool>::operator[]`, ainsi que deux erreurs courantes de programmation commentées. Des erreurs sont alors provoquées, car l'adresse de l'objet `vector<bool>::reference` retourné par `vector<bool>::operator[]` ne peut pas être acceptée.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="pointer"></a>  vector\<bool>::pointer

Type qui décrit un objet pouvant servir de pointeur pour un élément booléen de la séquence contenue dans l'objet `vector<bool>`.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>  vector\<bool>::reference, classe

La classe `vector<bool>::reference` est une classe proxy fournie par la [classe vector\<bool>](../standard-library/vector-bool-class.md) pour simuler `bool&`.

### <a name="remarks"></a>Notes

Une référence simulée est requise car C++ n'autorise pas en mode natif les références directes aux bits. `vector<bool>` utilise un seul bit par élément, lequel peut être référencé à l'aide de cette classe proxy. Toutefois, la simulation de référence n'est pas terminée car certaines attributions ne sont pas valides. Par exemple, comme l’adresse de l’objet `vector<bool>::reference` ne peut pas être prise, le code suivant qui utilise [vector\<bool>::operator&#91;&#93;](#op_at) n’est pas correct :

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>  vector\<bool>::reference::flip

Inverse la valeur booléenne d’un élément [vector\<bool>](../standard-library/vector-bool-class.md) référencé.

```cpp
void flip();
```

#### <a name="example"></a>Exemple

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

###  <a name="reference_operator_bool"></a>  vector\<bool>::reference::operator bool

Fournit une conversion implicite `vector<bool>::reference` de en **bool**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Valeur de retour

La valeur booléenne de l’élément de l’objet vector\<bool>.

#### <a name="remarks"></a>Notes

L'objet `vector<bool>` ne peut pas être modifié par cet opérateur.

###  <a name="reference_operator_eq"></a>  vector\<bool>::reference::operator=

Assigne une valeur booléenne à un bit, ou la valeur détenue par un élément référencé à un bit.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence d'élément dont la valeur doit être assignée au bit.

*Multiples*\
Valeur booléenne à assigner au bit.

#### <a name="example"></a>Exemple

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="swap"></a>  vector\<bool>::swap

Fonction membre statique qui échange deux éléments de vecteurs booléens (`vector<bool>`) à l’aide de la classe proxy [vector\<bool>::reference](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Élément à échanger avec l’élément *approprié* .

*Oui*\
Élément à échanger avec l’élément de *gauche* .

### <a name="remarks"></a>Notes

Cette surcharge prend en charge les spécifications spéciales de proxy de `vector<bool>`. [vector](../standard-library/vector-class.md)::swap a les mêmes fonctionnalités que la surcharge à un seul argument de `vector<bool>::swap()`.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
