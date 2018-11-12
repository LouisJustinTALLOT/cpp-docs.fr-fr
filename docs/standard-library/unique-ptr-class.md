---
title: unique_ptr, classe
ms.date: 11/04/2016
f1_keywords:
- memory/std::unique_ptr
- memory/std::unique_ptr::deleter_type
- memory/std::unique_ptr::element_type
- memory/std::unique_ptr::pointer
- memory/std::unique_ptr::get
- memory/std::unique_ptr::get_deleter
- memory/std::unique_ptr::release
- memory/std::unique_ptr::reset
- memory/std::unique_ptr::swap
helpviewer_keywords:
- std::unique_ptr [C++]
- std::unique_ptr [C++], deleter_type
- std::unique_ptr [C++], element_type
- std::unique_ptr [C++], pointer
- std::unique_ptr [C++], get
- std::unique_ptr [C++], get_deleter
- std::unique_ptr [C++], release
- std::unique_ptr [C++], reset
- std::unique_ptr [C++], swap
ms.assetid: acdf046b-831e-4a4a-83aa-6d4ee467db9a
ms.openlocfilehash: 00a29fc22c07cf54d4a26cd3353deef0b7a88acc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642193"
---
# <a name="uniqueptr-class"></a>unique_ptr, classe

Stocke un pointeur vers un objet ou un tableau détenu. L'objet/tableau n'est détenu par aucun autre `unique_ptr`. L'objet/tableau est détruit quand `unique_ptr` est détruit.

## <a name="syntax"></a>Syntaxe

```cpp
class unique_ptr {
public:
    unique_ptr();
    unique_ptr(nullptr_t Nptr);
    explicit unique_ptr(pointer Ptr);
    unique_ptr(pointer Ptr,
        typename conditional<is_reference<Del>::value, Del,
        typename add_reference<const Del>::type>::type Deleter);
    unique_ptr(pointer Ptr,
        typename remove_reference<Del>::type&& Deleter);
    unique_ptr(unique_ptr&& Right);
    template <class T2, Class Del2>
    unique_ptr(unique_ptr<T2, Del2>&& Right);
    unique_ptr(const unique_ptr& Right) = delete;
    unique_ptr& operator=(const unique_ptr& Right) = delete;
};

//Specialization for arrays:
template <class T, class D>
class unique_ptr<T[], D> {
public:
    typedef pointer;
    typedef T element_type;
    typedef D deleter_type;
    constexpr unique_ptr() noexcept;
    template <class U>
    explicit unique_ptr(U p) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    template <class U>
    unique_ptr(U p, see below d) noexcept;
    unique_ptr(unique_ptr&& u) noexcept;
    constexpr unique_ptr(nullptr_t) noexcept : unique_ptr() { }     template <class U, class E>
        unique_ptr(unique_ptr<U, E>&& u) noexcept;
    ~unique_ptr();
    unique_ptr& operator=(unique_ptr&& u) noexcept;
    template <class U, class E>
    unique_ptr& operator=(unique_ptr<U, E>&& u) noexcept;
    unique_ptr& operator=(nullptr_t) noexcept;
    T& operator[](size_t i) const;

    pointer get() const noexcept;
    deleter_type& get_deleter() noexcept;
    const deleter_type& get_deleter() const noexcept;
    explicit operator bool() const noexcept;
    pointer release() noexcept;
    void reset(pointer p = pointer()) noexcept;
    void reset(nullptr_t = nullptr) noexcept;
    template <class U>
    void reset(U p) noexcept = delete;
    void swap(unique_ptr& u) noexcept;  // disable copy from lvalue unique_ptr(const unique_ptr&) = delete;
    unique_ptr& operator=(const unique_ptr&) = delete;
};
```

### <a name="parameters"></a>Paramètres

*Droite*<br/>
`unique_ptr`

*Nptr*<br/>
`rvalue` de type `std::nullptr_t`.

*PTR*<br/>
`pointer`

*SUPPRESSEUR*<br/>
Fonction `deleter` liée à un `unique_ptr`.

## <a name="exceptions"></a>Exceptions

Aucune exception n'est générée par `unique_ptr`.

## <a name="remarks"></a>Notes

La classe `unique_ptr` remplace `auto_ptr` et peut être utilisée comme élément des conteneurs de bibliothèque standard C++.

Utilisez la fonction d’assistance [make_unique](../standard-library/memory-functions.md#make_unique) pour créer efficacement de nouvelles instances de `unique_ptr`.

`unique_ptr` gère de façon unique une ressource. Chaque objet `unique_ptr` stocke un pointeur vers l'objet qu'il possède ou stocke un pointeur null. Une ressource ne peut pas être détenue par plus d’un objet `unique_ptr`. Lorsqu’un objet `unique_ptr` qui possède une ressource particulière est détruit, la ressource est libérée. Un objet `unique_ptr` peut être déplacé, mais pas copié. Pour plus d’informations, consultez [Déclarateur de référence Rvalue : &&](../cpp/rvalue-reference-declarator-amp-amp.md).

La ressource est libérée par l'appel à un objet `deleter` stocké de type `Del` qui sait comment les ressources sont allouées pour un `unique_ptr` particulier. La valeur par défaut `deleter` `default_delete<T>` suppose que la ressource désignée par `ptr` est alloué avec `new`, et qu’elle peut être libérée en appelant `delete _Ptr`. (Une spécialisation partielle `unique_ptr<T[]>` gère les objets tableaux alloués à `new[]`, et possède le `deleter` `default_delete<T[]>` par défaut, spécialisé pour appeler delete[] `ptr`.)

Le pointeur stocké vers une ressource détenue, `stored_ptr`, a le type `pointer`. Il s’agit de `Del::pointer` s’il est défini, ou de `T *` dans le cas contraire. L'objet `deleter` stocké `stored_deleter` n'occupe pas d'espace dans l'objet si le `deleter` est sans état. Notez que `Del` peut être un type référence.

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[unique_ptr](#unique_ptr)|Il existe sept constructeurs pour `unique_ptr`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[deleter_type](#deleter_type)|Synonyme pour le paramètre du modèle `Del`.|
|[element_type](#element_type)|Synonyme pour le paramètre du modèle `T`.|
|[pointer](#pointer)|Synonyme pour `Del::pointer` s'il est défini ; sinon `T *`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[get](#get)|Retourne `stored_ptr`.|
|[get_deleter](#get_deleter)|Retourne une référence à `stored_deleter`.|
|[release](#release)|Stocke `pointer()` dans `stored_ptr` et retourne son contenu précédent.|
|[reset](#reset)|Libère la ressource détenue actuellement et accepte une nouvelle ressource.|
|[swap](#swap)|Échange la ressource et `deleter` avec l'objet `unique_ptr` fourni.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|**operator bool**|L’opérateur retourne une valeur d’un type convertible en **bool**. Le résultat de la conversion en **bool** est **true** lorsque `get() != pointer()`, sinon **false**.|
|`operator->`|La fonction membre retourne `stored_ptr`.|
|`operator*`|La fonction membre retourne `*stored_ptr`.|
|[unique_ptr operator=](#unique_ptr_operator_eq)|Assigne la valeur d’un objet `unique_ptr` (ou d’un `pointer-type`) à l’objet `unique_ptr` actuel.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<memory>

**Espace de noms :** std

## <a name="deleter_type"></a>  deleter_type

Le type est un synonyme du paramètre de modèle `Del`.

```cpp
typedef Del deleter_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Del`.

## <a name="element_type"></a>  element_type

Le type est un synonyme du paramètre de modèle `Type`.

```cpp
typedef Type element_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Ty`.

## <a name="get"></a>  unique_ptr::get

Retourne `stored_ptr`.

```cpp
pointer get() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne `stored_ptr`.

## <a name="get_deleter"></a>  unique_ptr::get_deleter

Retourne une référence à `stored_deleter`.

```cpp
Del& get_deleter();

const Del& get_deleter() const;
```

### <a name="remarks"></a>Notes

La fonction membre retourne une référence à `stored_deleter`.

## <a name="unique_ptr_operator_eq"></a>  unique_ptr operator=

Affecte l'adresse du `unique_ptr` fourni à l'objet actif.

```cpp
unique_ptr& operator=(unique_ptr&& right);
template <class U, Class Del2>
unique_ptr& operator=(unique_ptr<Type, Del>&& right);
unique_ptr& operator=(pointer-type);
```

### <a name="parameters"></a>Paramètres

Référence `unique_ptr` utilisée pour affecter la valeur au `unique_ptr` actif.

### <a name="remarks"></a>Notes

Les fonctions membres appellent `reset(right.release())` et déplacent `right.stored_deleter` vers `stored_deleter`, puis retournent `*this`.

## <a name="pointer"></a>  pointer

Synonyme pour `Del::pointer` s'il est défini ; sinon `Type *`.

```cpp
typedef T1 pointer;
```

### <a name="remarks"></a>Notes

Le type est un synonyme de `Del::pointer` s'il est défini ; sinon `Type *`.

## <a name="release"></a>  unique_ptr::release

Libère la propriété du pointeur stocké retourné à l’appelant et définit la valeur de pointeur stocké sur **nullptr**.

```cpp
pointer release();
```

### <a name="remarks"></a>Notes

Utilisez `release` pour prendre possession du pointeur brut stocké par le pointeur `unique_ptr`. L'appelant est responsable de la suppression du pointeur retourné. Le pointeur `unique-ptr` est défini sur l'état construit par défaut vide. Vous pouvez affecter un autre pointeur de type compatible au pointeur `unique_ptr` après l'appel à `release`.

### <a name="example"></a>Exemple

Cet exemple montre comment l’appelant de release est responsable de l’objet retourné :

```cpp
// stl_release_unique.cpp
// Compile by using: cl /W4 /EHsc stl_release_unique.cpp
#include <iostream>
#include <memory>

struct Sample {
   int content_;
   Sample(int content) : content_(content) {
      std::cout << "Constructing Sample(" << content_ << ")" << std::endl;
   }
   ~Sample() {
      std::cout << "Deleting Sample(" << content_ << ")" << std::endl;
   }
};

void ReleaseUniquePointer() {
   // Use make_unique function when possible.
   auto up1 = std::make_unique<Sample>(3);
   auto up2 = std::make_unique<Sample>(42);

   // Take over ownership from the unique_ptr up2 by using release
   auto ptr = up2.release();
   if (up2) {
      // This statement does not execute, because up2 is empty.
      std::cout << "up2 is not empty." << std::endl;
   }
   // We are now responsible for deletion of ptr.
   delete ptr;
   // up1 deletes its stored pointer when it goes out of scope.
}

int main() {
   ReleaseUniquePointer();
}
```

Sortie de l'ordinateur :

```Output
Constructing Sample(3)
Constructing Sample(42)
Deleting Sample(42)
Deleting Sample(3)

```

## <a name="reset"></a>  unique_ptr::reset

Prend possession du paramètre de pointeur et supprime le pointeur stocké d'origine. Si le nouveau pointeur est le même que le pointeur stocké d’origine, `reset` supprime le pointeur et définit le pointeur stocké sur **nullptr**.

```cpp
void reset(pointer ptr = pointer());
void reset(nullptr_t ptr);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers la ressource dont il faut prendre possession.|

### <a name="remarks"></a>Notes

Utilisez `reset` pour attribuer au [pointeur](#pointer) détenus par le `unique_ptr` à *ptr* , puis supprimez le pointeur stocké d’origine. Si l’objet `unique_ptr` n’était pas vide, `reset` appelle la fonction de suppression retournée par [get_deleter](#get_deleter) sur le pointeur stocké d’origine.

Étant donné que `reset` stocke tout d’abord le nouveau pointeur *ptr*, puis supprime le pointeur stocké d’origine, il est possible pour `reset` supprimer immédiatement *ptr* si elle est identique à l’original pointeur stocké.

## <a name="swap"></a>  unique_ptr::swap

Échange des pointeurs entre deux objets `unique_ptr`.

```cpp
void swap(unique_ptr& right);
```

### <a name="parameters"></a>Paramètres

*right*<br/>
`unique_ptr` utilisé pour échanger des pointeurs.

### <a name="remarks"></a>Notes

La fonction membre échange `stored_ptr` avec `right.stored_ptr` et `stored_deleter` avec `right.stored_deleter`.

## <a name="unique_ptr"></a>  unique_ptr::unique_ptr

Il existe sept constructeurs pour `unique_ptr`.

```cpp
unique_ptr();

unique_ptr(nullptr_t);
explicit unique_ptr(pointer ptr);

unique_ptr(
    Type* ptr,
    typename conditional<
    is_reference<Del>::value,
    Del,
    typename add_reference<const Del>::type>::type _Deleter);

unique_ptr(pointer ptr, typename remove_reference<Del>::type&& _Deleter);
unique_ptr(unique_ptr&& right);
template <class Ty2, Class Del2>
unique_ptr(unique_ptr<Ty2, Del2>&& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*ptr*|Pointeur vers la ressource à affecter à un `unique_ptr.`|
|*_Deleter*|`deleter` à affecter à un `unique_ptr`.|
|*right*|`rvalue reference` à un `unique_ptr` à partir duquel des champs `unique_ptr` sont affectés par déplacement au `unique_ptr` nouvellement construit.|

### <a name="remarks"></a>Notes

Les deux premiers constructeurs construisent un objet qui ne gère aucune ressource. Le troisième constructeur stocke *ptr* dans `stored_ptr`. Le quatrième constructeur stocke *ptr* dans `stored_ptr` et `deleter` dans `stored_deleter`.

Le cinquième constructeur stocke *ptr* dans `stored_ptr` et déplace `deleter` dans `stored_deleter`. Les sixième et septième constructeurs stockent `right.release()` dans `stored_ptr` et déplacent `right.get_deleter()` dans `stored_deleter`.

## <a name="dtorunique_ptr"></a>  unique_ptr ~unique_ptr

Destructeur de `unique_ptr`. Détruit un objet `unique_ptr`.

```cpp
~unique_ptr();
```

### <a name="remarks"></a>Notes

Le destructeur appelle `get_deleter()(stored_ptr)`.

## <a name="see-also"></a>Voir aussi

[\<memory>](../standard-library/memory.md)<br/>
