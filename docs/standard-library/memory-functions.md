---
title: '&lt;memory&gt;, fonctions'
ms.date: 08/05/2019
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.openlocfilehash: 2aceb96fcda49df8a1fd40a1bd8011170dccd8ef
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687725"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt;, fonctions

## <a name="addressof"></a>AddressOf

Obtient l'adresse exacte d'un objet.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>Paramètres

*value*\
Objet ou fonction desquels obtenir l'adresse exacte.

### <a name="return-value"></a>Valeur de retour

Adresse réelle de l’objet ou de la fonction référencée par *valeur*, même si un `operator&()` surchargé existe.

### <a name="remarks"></a>Notes

## <a name="align"></a>droite

Ajuste le stockage de la taille donnée, alignée par la spécification d’alignement donnée, à la première adresse possible du stockage donné.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>Paramètres

\ d' *alignement*
Limite d'alignement à tenter.

*taille* \
Taille en octets du stockage aligné.

\ *ptr*
Adresse de départ du pool de stockage contigu disponible à utiliser. Ce paramètre est également un paramètre de sortie qui est défini pour contenir la nouvelle adresse de départ si l’alignement est réussi. Si `align()` échoue, ce paramètre n’est pas modifié.

*espace* \
Espace total disponible pour `align()` pour la création du stockage aligné. Ce paramètre est également un paramètre de sortie. Il contient l'espace ajusté restant dans la mémoire tampon de stockage une fois le stockage aligné et toute surcharge associée soustraite.

Si `align()` échoue, ce paramètre n’est pas modifié.

### <a name="return-value"></a>Valeur de retour

Pointeur null si la mémoire tampon alignée demandée ne tient pas dans l’espace disponible ; Sinon, la nouvelle valeur de *ptr*.

### <a name="remarks"></a>Notes

Les paramètres *ptr* et *Space* modifiés vous permettent d’appeler `align()` à plusieurs reprises sur la même mémoire tampon, éventuellement avec des valeurs différentes pour l' *alignement* et la *taille*. L'extrait de code suivant illustre une utilisation de `align()`.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>allocate_shared

Crée un [shared_ptr](shared-ptr-class.md) pour les objets qui sont alloués et construits pour un type donné à l’aide d’un allocateur spécifié. Retourne l'`shared_ptr`.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

\ *Alloc*
Allocateur utilisé pour créer les objets.

*arguments* \
Zéro ou plusieurs arguments qui deviennent les objets.

### <a name="remarks"></a>Notes

La fonction crée l’objet `shared_ptr<T>`, un pointeur vers `T(args...)` comme alloué et construit par *Alloc*.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Conversion const en [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Paramètres

*T* \
Type contrôlé par le pointeur partagé retourné.

*Autres* \
Type contrôlé par le pointeur partagé d’argument.

*sp* \
Pointeur partagé d’argument.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un objet `shared_ptr` vide si `const_cast<T*>(sp.get())` retourne un pointeur null ; dans le cas contraire, elle retourne un objet `shared_ptr<T>` qui possède la ressource détenue par *SP*. L'expression `const_cast<T*>(sp.get())` doit être valide.

### <a name="example"></a>Exemple

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

    *sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>declare_no_pointers

Informe un récupérateur de mémoire que les caractères dans le bloc de mémoire défini par un pointeur d’adresse de base et une taille de bloc ne contiennent aucun pointeur traçable.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Adresse du premier caractère qui ne contient plus de pointeur traçable.

*taille* \
Taille du bloc qui commence à *ptr* et qui ne contient pas de pointeurs traçables.

### <a name="remarks"></a>Notes

La fonction informe tout garbage collector que les adresses de la plage `[ ptr, ptr + size)` ne contiennent plus de pointeurs traçables. (Tous les pointeurs vers des stockages alloués ne doivent pas être déréférencés, sauf s’ils sont accessibles.)

## <a name="declare_reachable"></a>declare_reachable

Informe une opération garbage collection que l’adresse indiquée est dédiée au stockage alloué et est accessible.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Pointeur vers une zone de stockage accessible, allouée et valide.

### <a name="remarks"></a>Notes

Si *ptr* n’a pas la valeur null, la fonction informe tout garbage collector que *ptr* est désormais accessible, c’est-à-dire qu’il pointe vers un stockage alloué valide.

## <a name="default_delete"></a>default_delete

Supprime les objets alloués avec l' **opérateur New**. Adapté à une utilisation avec [unique_ptr](unique-ptr-class.md).

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Pointeur vers l'objet à supprimer.

*Autres* \
Type des éléments dans le tableau à supprimer.

### <a name="remarks"></a>Notes

Le modèle de classe décrit un effaceur qui supprime les objets scalaires alloués avec l' **opérateur New**, approprié pour une utilisation avec le modèle de classe `unique_ptr`. Il possède également la spécialisation explicite `default_delete<T[]>`.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

Comme pour `location->~T()`.

## <a name="destroy"></a>suppression

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

Identique à :

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

Identique à :

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Cast dynamique en [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Paramètres

*T* \
Type contrôlé par le pointeur partagé retourné.

*Autres* \
Type contrôlé par le pointeur partagé d’argument.

*sp* \
Pointeur partagé d’argument.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un objet `shared_ptr` vide si `dynamic_cast<T*>(sp.get())` retourne un pointeur null ; dans le cas contraire, elle retourne un objet `shared_ptr<T>` qui possède la ressource détenue par *SP*. L'expression `dynamic_cast<T*>(sp.get())` doit être valide.

### <a name="example"></a>Exemple

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

Récupérez le supprimer à partir d’un [shared_ptr](shared-ptr-class.md).

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>Paramètres

@No__t_1 de la *suppression*
Type du suppresseur.

*T* \
Type contrôlé par le pointeur partagé.

*sp* \
Pointeur partagé.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un pointeur vers le supprimer du type de *suppression* qui appartient à l’objet `shared_ptr` *SP*. Si *SP* n’a pas de suppression, ou si son supprimeur n’est pas de type *supprimer*, la fonction retourne 0.

### <a name="example"></a>Exemple

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

Retourne le type de sécurité de pointeur supposé par tout récupérateur de mémoire.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Notes

La fonction retourne le type de sécurité de pointeur supposé par tout garbage collector automatique.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Alloue un stockage temporaire pour une séquence d’éléments qui ne dépasse pas un nombre spécifié d’éléments.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>Paramètres

*nombre* \
Nombre maximal d’éléments demandés pour lesquels la mémoire doit être allouée.

### <a name="return-value"></a>Valeur de retour

`pair` dont le premier composant est un pointeur vers la mémoire qui a été allouée, et dont le deuxième composant donne la taille de la mémoire tampon, indiquant le nombre d’éléments le plus élevé qu’elle puisse stocker.

### <a name="remarks"></a>Notes

La fonction effectue une demande de mémoire qui présente des risques d’échec. Si aucune mémoire tampon n’est allouée, la fonction retourne une paire dans laquelle le deuxième élément est égal à zéro et le premier élément est égal au pointeur Null.

Utilisez cette fonction uniquement pour la mémoire temporaire.

### <a name="example"></a>Exemple

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
        << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>make_shared

Crée et retourne un [shared_ptr](shared-ptr-class.md) qui pointe vers les objets alloués qui sont construits à partir de zéro ou de plusieurs arguments à l’aide de l’allocateur par défaut. Alloue et construit un objet du type spécifié et un pointeur `shared_ptr` pour gérer une propriété partagée de l'objet et retourne le pointeur `shared_ptr`.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>Paramètres

*arguments* \
Zéro ou plusieurs arguments de constructeur. Selon les arguments fournis, la fonction déduit la surcharge de constructeur à appeler.

### <a name="remarks"></a>Notes

Utilisez `make_shared` comme un moyen simple et plus efficace pour créer un objet et un pointeur `shared_ptr` pour gérer l'accès partagé à l'objet en même temps. Sémantiquement, les deux instructions suivantes sont équivalentes :

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Toutefois, la première instruction crée deux allocations, et si l'allocation du pointeur `shared_ptr` échoue alors que l'allocation de l'objet `Example` a réussi, l'objet sans nom `Example` est victime d'une fuite. L'instruction qui utilise `make_shared` est plus simple car un seul appel de fonction est impliqué. Elle est plus efficace car la bibliothèque peut effectuer une allocation unique pour l'objet et le pointeur intelligent. Cette fonction est à la fois plus rapide et provoque moins de fragmentation de la mémoire, et il n’y a aucun risque d’exception sur une allocation, mais pas sur l’autre. Les performances sont améliorées grâce à une meilleure localité du code qui fait référence à l'objet et qui met à jour les décomptes de références dans le pointeur intelligent.

Envisagez d’utiliser [make_unique](memory-functions.md#make_unique) si vous n’avez pas besoin d’un accès partagé à l’objet. Utilisez [allocate_shared](memory-functions.md#allocate_shared) si vous devez spécifier un allocateur personnalisé pour l’objet. Vous ne pouvez pas utiliser `make_shared` si votre objet nécessite un effaceur personnalisé, car il n’existe aucun moyen de passer le supprimeur en tant qu’argument.

L'exemple suivant illustre la création de pointeurs partagés vers un type en appelant des surcharges de constructeur spécifiques.

### <a name="example"></a>Exemple

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
    std::wstring title_;
    std::wstring artist_;

    Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
    Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers()
{
    // Okay, but less efficient to have separate allocations for
    // Song object and shared_ptr control block.
    auto song = new Song(L"Ode to Joy", L"Beethoven");
    std::shared_ptr<Song> sp0(song);

    // Use make_shared function when possible. Memory for control block
    // and Song object are allocated in the same call:
    auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
    auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

    // make_shared infers which constructor to use based on the arguments.
    auto sp3 = std::make_shared<Song>(L"Greensleeves");

    // The playlist vector makes copies of the shared_ptr pointers.
    std::vector<std::shared_ptr<Song>> playlist;
    playlist.push_back(sp0);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    playlist.push_back(sp3);
    playlist.push_back(sp1);
    playlist.push_back(sp2);
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

L'exemple génère cette sortie :

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

Crée et retourne un [unique_ptr](unique-ptr-class.md) vers un objet du type spécifié, qui est construit à l’aide des arguments spécifiés.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>Paramètres

*T* \
Type de l’objet vers lequel pointera le `unique_ptr`.

*Arguments* \
Types des arguments de constructeur spécifiés par *args*.

*arguments* \
Arguments à passer au constructeur de l’objet de type *T*.

*éléments* \
Tableau d’éléments de type *T*.

*taille* \
Nombre d’éléments pour lesquels allouer de l’espace dans le nouveau tableau.

### <a name="remarks"></a>Notes

La première surcharge est utilisée pour les objets uniques. La deuxième surcharge est appelée pour les tableaux. La troisième surcharge vous empêche de spécifier une taille de tableau dans l’argument de type (make_unique \<T [N] >); Cette construction n’est pas prise en charge par la norme actuelle. Quand vous utilisez `make_unique` pour créer un `unique_ptr` dans un tableau, vous devez initialiser les éléments du tableau séparément. Au lieu d’utiliser cette surcharge, il est peut-être préférable d’utiliser un [std :: Vector](vector-class.md).

`make_unique` étant implémentée soigneusement pour la protection contre les exceptions, nous vous recommandons d’utiliser `make_unique` au lieu d’appeler directement des constructeurs `unique_ptr`.

### <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser `make_unique`. Pour obtenir plus d’exemples, consultez [Guide pratique pour créer et utiliser des instances unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Quand vous voyez l’erreur C2280 en lien avec `unique_ptr`, il est presque certain que vous essayez d’appeler son constructeur de recopie, qui est une fonction supprimée.

## <a name="owner_less"></a>owner_less

Permet des comparaisons mixtes basées sur la propriété de pointeurs partagés et faibles. Retourne la **valeur true** si le paramètre de gauche est ordonné avant le paramètre Right par la fonction membre `owner_before`.

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>Paramètres

\ *gauche*
Pointeur partagé ou faible.

\ *droit*
Pointeur partagé ou faible.

### <a name="remarks"></a>Notes

Les modèles de classe définissent tous leurs opérateurs membres comme renvoyant des `left.owner_before(right)`.

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

Crée un `shared_ptr` à partir d’un pointeur partagé existant à l’aide d’un cast.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Référence à un `shared_ptr<U>`.

### <a name="remarks"></a>Notes

Si *ptr* est vide, le nouveau `shared_ptr` est également vide, sinon il partage la propriété avec *ptr*. Le nouveau pointeur partagé est le résultat de l’évaluation de `reinterpret_cast<Y*>(ptr.get())`, où `Y` est `typename std::shared_ptr<T>::element_type`. Le comportement n’est pas défini si `reinterpret_cast<T*>((U*)nullptr)` n’est pas bien formé.

La fonction de modèle qui accepte une référence lvalue est nouvelle dans C++ 17. La fonction de modèle qui accepte une référence rvalue est nouvelle dans C++ 20.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Libère la mémoire temporaire allouée à l'aide de la fonction de modèle `get_temporary_buffer`.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>Paramètres

\ de la *mémoire tampon*
Pointeur vers la mémoire à libérer.

### <a name="remarks"></a>Notes

Utilisez cette fonction uniquement pour la mémoire temporaire.

### <a name="example"></a>Exemple

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
    // Create an array of ints
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
    int count = sizeof ( intArray ) / sizeof ( int );
    cout << "The number of integers in the array is: "
         << count << "." << endl;

    pair<int *, ptrdiff_t> resultPair;
    resultPair = get_temporary_buffer<int>( count );

    cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

    int* tempBuffer = resultPair.first;

    // Deallocates memory allocated with get_temporary_buffer
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

Cast statique en [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Paramètres

*T* \
Type contrôlé par le pointeur partagé retourné.

*Autres* \
Type contrôlé par le pointeur partagé d’argument.

*sp* \
Pointeur partagé d’argument.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un objet `shared_ptr` vide si *SP* est un objet `shared_ptr` vide. dans le cas contraire, elle retourne un objet `shared_ptr<T>` qui possède la ressource détenue par *SP*. L'expression `static_cast<T*>(sp.get())` doit être valide.

### <a name="example"></a>Exemple

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>échange

Échangez deux objets [shared_ptr](shared-ptr-class.md), [unique_ptr](unique-ptr-class.md)ou [weak_ptr](weak-ptr-class.md) .

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>Paramètres

*T* \
Type contrôlé par le pointeur d’argument.

@No__t_1 de la *suppression*
Suppression du type de pointeur unique.

\ *gauche*
Pointeur gauche.

\ *droit*
Pointeur droit.

### <a name="remarks"></a>Notes

Les fonctions de modèle appellent `left.swap(right)`.

### <a name="example"></a>Exemple

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

Informe un récupérateur de mémoire que les caractères dans le bloc de mémoire défini par un pointeur d'adresse de base et une taille de bloc peuvent maintenant contenir des pointeurs traçables.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Pointeur vers l’adresse mémoire précédemment marquée à l’aide de [declare_no_pointers](#declare_no_pointers).

*taille* \
Nombre d’octets dans la plage de mémoire. Cette valeur doit être égale au nombre utilisé dans l’appel de `declare_no_pointers`.

### <a name="remarks"></a>Notes

La fonction informe tout garbage collector que la plage d’adresses `[ptr, ptr + size)` peut maintenant contenir des pointeurs traçables.

## <a name="undeclare_reachable"></a>undeclare_reachable

Révoque une déclaration d’accessibilité pour un emplacement de mémoire spécifié.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>Paramètres

\ *ptr*
Pointeur vers l’adresse mémoire précédemment marquée à l’aide de [declare_reachable](#declare_reachable).

### <a name="remarks"></a>Notes

Si *ptr* n’est pas **nullptr**, la fonction informe tout garbage collector que *ptr* n’est plus accessible. Elle retourne un pointeur dérivé en toute sécurité qui correspond à *ptr*.

## <a name="uninitialized_copy"></a>uninitialized_copy

Copie les objets d'une plage source spécifiée dans une plage de destination non initialisée.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur d'entrée qui traite le premier élément de la plage source.

*dernier* \
Itérateur d'entrée qui traite le dernier élément de la plage source.

*dest* \
Itérateur vers l’avant qui traite le premier élément de la plage de destination.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la première position au-delà de la plage de destination, sauf si la plage source est vide.

### <a name="remarks"></a>Notes

Cet algorithme permet de découpler l'allocation de mémoire et la construction d'objet.

La fonction de modèle est exécutée :

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

La surcharge avec une stratégie d’exécution est nouvelle dans C++ 17.

### <a name="example"></a>Exemple

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

Crée une copie d'un nombre spécifié d'éléments à partir d'un itérateur d'entrée. Les copies sont placées dans un itérateur forward.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur d'entrée qui fait référence à l'objet à copier.

*nombre* \
Type entier signé ou non signé spécifiant le nombre de fois que l'objet doit être copié.

*dest* \
Itérateur vers l’avant qui fait référence à l'emplacement des nouvelles copies.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la première position au-delà de la destination. Si la plage source est vide, l’itérateur s’adresse en *premier*.

### <a name="remarks"></a>Notes

La fonction de modèle exécute efficacement le code suivant :

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

La surcharge avec une stratégie d’exécution est nouvelle dans C++ 17.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

Construit par défaut les objets des itérateurs' `value_type` dans la plage spécifiée.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur qui traite le premier élément de la plage à construire.

*dernier* \
Itérateur qui traite un après le dernier élément de la plage à construire.

### <a name="remarks"></a>Notes

La version sans stratégie d’exécution est la même que celle-ci :

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

Si une exception est levée, les objets construits précédemment sont détruits dans un ordre non spécifié.

La version avec une stratégie d’exécution a le même résultat, mais s’exécute en fonction de la *stratégie*spécifiée.

Ces fonctions sont nouvelles dans C++ 17.

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

La valeur par défaut construit un nombre spécifié d’objets du `value_type` de l’itérateur, en commençant à l’emplacement spécifié.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur qui traite le premier élément de la plage de destination à construire.

*nombre* \
Nombre d’éléments dans la plage de destination à construire.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la première position au-delà de la plage de destination, sauf si la plage source est vide.

### <a name="remarks"></a>Notes

La version sans stratégie d’exécution est la même que celle-ci :

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

Si une exception est levée, les objets construits précédemment sont détruits dans un ordre non spécifié.

La version avec une stratégie d’exécution a le même résultat, mais s’exécute en fonction de la *stratégie*spécifiée.

Ces fonctions sont nouvelles dans C++ 17.

## <a name="uninitialized_fill"></a>uninitialized_fill

Copie les objets d'une valeur spécifiée dans une plage de destination non initialisée.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur vers l’avant qui traite le premier élément de la plage de destination à initialiser.

*dernier* \
Itérateur vers l’avant qui traite le dernier élément de la plage de destination à initialiser.

*value*\
Valeur à utiliser pour initialiser la plage de destination.

### <a name="remarks"></a>Notes

Cet algorithme permet de découpler l'allocation de mémoire et la construction d'objet.

La fonction de modèle est exécutée :

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

La surcharge avec une stratégie d’exécution est nouvelle dans C++ 17.

### <a name="example"></a>Exemple

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Copie les objets d’une valeur spécifiée dans le nombre spécifié d’éléments d’une plage de destination non initialisée.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur vers l’avant qui traite le premier élément de la plage de destination à initialiser.

*nombre* \
Nombre d’éléments à initialiser.

*value*\
Valeur à utiliser pour initialiser la plage de destination.

### <a name="remarks"></a>Notes

Cet algorithme permet de découpler l'allocation de mémoire et la construction d'objet.

La fonction de modèle est exécutée :

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

La surcharge avec une stratégie d’exécution est nouvelle dans C++ 17.

### <a name="example"></a>Exemple

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

Déplace les éléments d’une plage source vers une zone de mémoire de destination non initialisée.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur d’entrée qui traite le premier élément de la plage source à déplacer.

*dernier* \
Itérateur d’entrée qui traite un après le dernier élément de la plage source à déplacer.

*dest* \
Début de la plage de destination.

### <a name="remarks"></a>Notes

La version sans stratégie d’exécution est la même que celle-ci :

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

Si une exception est levée, certains objets de la plage source peuvent être laissés dans un état valide mais non spécifié. Les objets construits précédemment sont détruits dans un ordre non spécifié.

La version avec une stratégie d’exécution a le même résultat, mais s’exécute en fonction de la *stratégie*spécifiée.

Ces fonctions sont nouvelles dans C++ 17.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

Déplace un nombre spécifié d’éléments d’une plage source vers une zone de mémoire de destination non initialisée.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur d’entrée qui traite le premier élément de la plage source à déplacer.

*nombre* \
Nombre d’éléments dans la plage source à déplacer.

*dest* \
Début de la plage de destination.

### <a name="remarks"></a>Notes

La version sans stratégie d’exécution est la même que celle-ci :

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

Si une exception est levée, certains objets de la plage source peuvent être laissés dans un état valide mais non spécifié. Les objets construits précédemment sont détruits dans un ordre non spécifié.

La version avec une stratégie d’exécution a le même résultat, mais s’exécute en fonction de la *stratégie*spécifiée.

Ces fonctions sont nouvelles dans C++ 17.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

Construit des objets des itérateurs' `value_type` par initialisation de valeur, dans la plage spécifiée.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur qui traite le premier élément de la plage à la construction de valeur.

*dernier* \
Itérateur qui traite un après le dernier élément de la construction de la plage à la valeur.

### <a name="remarks"></a>Notes

La version sans stratégie d’exécution est la même que celle-ci :

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

Si une exception est levée, les objets construits précédemment sont détruits dans un ordre non spécifié.

La version avec une stratégie d’exécution a le même résultat, mais s’exécute en fonction de la *stratégie*spécifiée.

Si un échec d’allocation de mémoire se produit, une exception `std::bad_alloc` est levée.

Ces fonctions sont nouvelles dans C++ 17.

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

Construit un nombre spécifié d’objets du `value_type` de l’itérateur par initialisation de valeur, en commençant à l’emplacement spécifié.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Paramètres

\ de *stratégie*
Stratégie d’exécution à utiliser.

*premier* \
Itérateur qui traite le premier élément de la plage de destination à construire.

*nombre* \
Nombre d’éléments dans la plage de destination à construire.

### <a name="remarks"></a>Notes

La version sans stratégie d’exécution est la même que celle-ci :

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

Si une exception est levée, les objets construits précédemment sont détruits dans un ordre non spécifié.

La version avec une stratégie d’exécution a le même résultat, mais s’exécute en fonction de la *stratégie*spécifiée.

Si un échec d’allocation de mémoire se produit, une exception `std::bad_alloc` est levée.

Ces fonctions sont nouvelles dans C++ 17.

## <a name="uses_allocator_v"></a>uses_allocator_v

Un modèle de variable d’assistance pour accéder à la valeur du modèle de `uses_allocator`.

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Voir aussi

[\<memory>](memory.md)
