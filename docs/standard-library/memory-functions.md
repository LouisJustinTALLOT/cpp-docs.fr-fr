---
title: '&lt;memory&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
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
dev_langs:
- C++
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 676f6522a5625103a00310c6ce5353ce40da9359
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862924"
---
# <a name="ltmemorygt-functions"></a>&lt;memory&gt;, fonctions

||||
|-|-|-|
|[addressof](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared](#make_shared)|
|[make_unique](#make_unique)|[owner_less](#owner_less)|[return_temporary_buffer](#return_temporary_buffer)|
|[static_pointer_cast](#static_pointer_cast)|[swap (Bibliothèque standard C++)](#swap)|[undeclare_no_pointers](#undeclare_no_pointers)|
|[undeclare_reachable](#undeclare_reachable)|[uninitialized_copy](#uninitialized_copy)|[uninitialized_copy_n](#uninitialized_copy_n)|
|[uninitialized_fill](#uninitialized_fill)|[uninitialized_fill_n](#uninitialized_fill_n)|

## <a name="addressof"></a>  addressof

Obtient l'adresse exacte d'un objet.

```cpp
template <class T>
T* addressof(T& Val);
```

### <a name="parameters"></a>Paramètres

`Val` L’objet ou la fonction pour laquelle obtenir l’adresse exacte.

### <a name="return-value"></a>Valeur de retour

Adresse réelle de l'objet ou de la fonction référencés par `Val`, même en cas de `operator&()` surchargé.

### <a name="remarks"></a>Notes

## <a name="align"></a>  align

Place le stockage de la taille donnée (aligné par la spécification d'alignement donnée) dans la première adresse possible du stockage donné.

```cpp
void* align(
    size_t Alignment, // input
    size_t Size,      // input
    void*& Ptr,        // input/output
    size_t& Space     // input/output
);
```

### <a name="parameters"></a>Paramètres

`Alignment` Limite d’alignement à tenter.

`Size` La taille en octets du stockage aligné.

`Ptr` Adresse de départ du pool de stockage contigu disponible à utiliser. Ce paramètre est également un paramètre de sortie et il est défini pour contenir la nouvelle adresse de départ si l’alignement est réussi. Si `align()` échoue, ce paramètre n'est pas modifié.

`Space` L’espace total disponible à `align()` à utiliser lors de la création du stockage aligné. Ce paramètre est également un paramètre de sortie. Il contient l'espace ajusté restant dans la mémoire tampon de stockage une fois le stockage aligné et toute surcharge associée soustraite.

Si `align()` échoue, ce paramètre n'est pas modifié.

### <a name="return-value"></a>Valeur de retour

Un pointeur null si la mémoire tampon alignée demandée est plus grande que l'espace disponible ; sinon, la nouvelle valeur de `Ptr`.

### <a name="remarks"></a>Notes

Les paramètres modifiés `Ptr` et `Space` permettent d'appeler `align()` à plusieurs reprises pour la même mémoire tampon, éventuellement avec des valeurs différentes pour `Alignment` et `Size`. L'extrait de code suivant illustre une utilisation de `align()`.

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

## <a name="allocate_shared"></a>  allocate_shared

Crée un `shared_ptr` pour les objets qui sont alloués et construits pour un type donné en utilisant un allocateur spécifié. Retourne l'`shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Paramètres

`Alloc` Allocateur utilisé pour créer des objets.

`Args` Les zéro ou plusieurs arguments qui deviennent les objets.

### <a name="remarks"></a>Notes

La fonction crée l’objet `shared_ptr<Type>`, un pointeur vers `Type(Args...)` tel qu’alloué et construit par `Alloc`.

## <a name="const_pointer_cast"></a>  const_pointer_cast

Cast de const en shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Paramètres

`Ty` Type contrôlé par le pointeur partagé retourné.

`Other` Type contrôlé par le pointeur partagé d’argument.

`Other` Pointeur partagé d’argument.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un objet shared_ptr vide si `const_cast<Ty*>(sp.get())` retourne un pointeur null ; sinon, elle retourne un [shared_ptr, classe](../standard-library/shared-ptr-class.md)\<Ty > objet qui détient la ressource appartenant à `sp`. L'expression `const_cast<Ty*>(sp.get())` doit être valide.

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

## <a name="declare_no_pointers"></a>  declare_no_pointers

Informe un récupérateur de mémoire que les caractères dans le bloc de mémoire défini par un pointeur d’adresse de base et une taille de bloc ne contiennent aucun pointeur traçable.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`ptr`|Adresse du premier caractère qui ne contient plus de pointeur traçable.|
|`_Size`|Taille du bloc qui commence à `ptr` qui ne contient aucun pointeur traçable.|

### <a name="remarks"></a>Notes

La fonction informe un RÉCUPÉRATEUR de mémoire que la plage d’adresses `[ ptr, ptr + _Size)` ne plus contenir des pointeurs traçables. (Tous les pointeurs vers le stockage alloué ne doivent pas être déréférencés sauf si rendu accessible.)

## <a name="declare_reachable"></a>  declare_reachable

Informe une opération garbage collection que l’adresse indiquée est dédiée au stockage alloué et est accessible.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Paramètres

`ptr` Pointeur vers une zone de stockage est accessible, alloué, valide.

### <a name="remarks"></a>Notes

Si `ptr` n’est pas Null, la fonction informe tout récupérateur de mémoire que `ptr` est dorénavant accessible (qu’il pointe vers du stockage alloué valide).

## <a name="default_delete"></a>  default_delete

Supprime les objets alloués avec `operator new`. Fonction pouvant être utilisée avec `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Paramètres

`Ptr` Pointeur vers l’objet à supprimer.

Autres le type des éléments du tableau doit être supprimé.

### <a name="remarks"></a>Notes

La classe de modèle décrit un `deleter` qui supprime les objets scalaires alloués avec `operator new`, utilisable avec la classe de modèle `unique_ptr`. Il possède également la spécialisation explicite `default_delete<Type[]>`.

## <a name="dynamic_pointer_cast"></a>  dynamic_pointer_cast

Cast dynamique en shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Paramètres

`Ty` Type contrôlé par le pointeur partagé retourné.

`Other` Type contrôlé par le pointeur partagé d’argument.

`sp` Pointeur partagé d’argument.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un objet shared_ptr vide si `dynamic_cast<Ty*>(sp.get())` retourne un pointeur null ; sinon, elle retourne un [shared_ptr, classe](../standard-library/shared-ptr-class.md)\<Ty > objet qui détient la ressource appartenant à `sp`. L'expression `dynamic_cast<Ty*>(sp.get())` doit être valide.

### <a name="example"></a>Exemple

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="get_deleter"></a>  get_deleter

Obtient un suppresseur à partir de shared_ptr.

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Paramètres

`D` Le type de la suppression.

`Ty` Type contrôlé par le pointeur partagé.

`sp` Le pointeur partagé.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un pointeur vers le suppresseur de type `D` qui appartient à l’objet `sp` de classe [shared_ptr](../standard-library/shared-ptr-class.md) . Si `sp` n’a aucun suppresseur ou si suppresseur n’est pas de type `D`, la fonction retourne 0.

### <a name="example"></a>Exemple

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct deleter
{
    void operator()(base *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->val = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->val = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}

```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>  get_pointer_safety

Retourne le type de sécurité de pointeur supposé par tout récupérateur de mémoire.

```cpp
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>Notes

La fonction retourne le type de sécurité de pointeur supposé par tout RÉCUPÉRATEUR de mémoire automatique.

## <a name="get_temporary_buffer"></a>  get_temporary_buffer

Alloue un stockage temporaire pour une séquence d'éléments qui ne dépasse pas un nombre spécifié d'éléments.

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Paramètres

`count` Le nombre maximal d’éléments demandés pour lesquels la mémoire doit être allouée.

### <a name="return-value"></a>Valeur de retour

`pair` dont le premier composant est un pointeur vers la mémoire qui a été allouée, et dont le deuxième composant donne la taille de la mémoire tampon, indiquant le nombre d’éléments le plus élevé qu’elle puisse stocker.

### <a name="remarks"></a>Notes

La fonction effectue une demande de mémoire qui présente des risques d’échec. Si aucune mémoire tampon n’est allouée, la fonction retourne une paire dans laquelle le deuxième élément est égal à zéro et le premier élément est égal au pointeur Null.

Cette fonction doit être utilisée uniquement pour la mémoire temporaire.

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
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

## <a name="make_shared"></a>  make_shared

Crée et retourne un pointeur `shared_ptr` qui pointe vers les objets alloués qui sont construits de zéro ou de plusieurs arguments à l'aide de l'allocateur par défaut. Alloue et construit un objet du type spécifié et un pointeur `shared_ptr` pour gérer une propriété partagée de l'objet et retourne le pointeur `shared_ptr`.

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`_Args`|Zéro ou plusieurs arguments de constructeur. Selon les arguments fournis, la fonction déduit la surcharge de constructeur à appeler.|

### <a name="remarks"></a>Notes

Utilisez `make_shared` comme un moyen simple et plus efficace pour créer un objet et un pointeur `shared_ptr` pour gérer l'accès partagé à l'objet en même temps. Sémantiquement, les deux instructions suivantes sont équivalentes :

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Toutefois, la première instruction crée deux allocations, et si l'allocation du pointeur `shared_ptr` échoue alors que l'allocation de l'objet `Example` a réussi, l'objet sans nom `Example` est victime d'une fuite. L'instruction qui utilise `make_shared` est plus simple car un seul appel de fonction est impliqué. Elle est plus efficace car la bibliothèque peut effectuer une allocation unique pour l'objet et le pointeur intelligent. Elle est plus rapide, elle entraîne moins de fragmentation de mémoire et aucune exception ne peut avoir lieu sur une allocation sans se produire également sur l'autre. Les performances sont améliorées grâce à une meilleure localité du code qui fait référence à l'objet et qui met à jour les décomptes de références dans le pointeur intelligent.

Utilisez plutôt [make_unique](../standard-library/memory-functions.md#make_unique) si vous n’avez pas besoin d’un accès partagé à l’objet. Utilisez [allocate_shared](../standard-library/memory-functions.md#allocate_shared) si vous devez spécifier un allocateur personnalisé pour l’objet. Vous ne pouvez pas utiliser `make_shared` si votre objet nécessite une suppression personnalisée, car il n'existe aucun moyen de transmettre la suppression en tant qu'argument.

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

void CreateSharedPointers() {
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
   for (auto&& sp : playlist) {
      std::wcout << L"Playing " << sp->title_ <<
         L" by " << sp->artist_ << L", use count: " <<
         sp.use_count() << std::endl;
   }
}

int main() {
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

## <a name="make_unique"></a>  make_unique

Crée et retourne un [unique_ptr](../standard-library/unique-ptr-class.md) vers un objet du type spécifié, qui est construit à l’aide des arguments spécifiés.

```cpp
// make_unique<T>
template <class T, class... Types>
unique_ptr<T>
make_unique(Types&&... Args)
{
    return (unique_ptr<T>(new T(forward<Types>(Args)...)));
}

// make_unique<T[]>
template <class T>
make_unique(size_t Size)
{
    return (unique_ptr<T>(new Elem[Size]()));
}

// make_unique<T[N]> disallowed
template <class T, class... Types>
typename enable_if<extent<T>::value != 0, void>::type
make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>Paramètres

`T` Le type de l’objet qui le `unique_ptr` pointera sur.

`Types` Les types des arguments de constructeur spécifiés par `Args`.

`Args` Les arguments à passer au constructeur de l’objet de type `T`.

`Elem` Un tableau d’éléments de type `T`.

`Size` Le nombre d’éléments d’allocation d’espace pour dans le nouveau tableau.

### <a name="remarks"></a>Notes

La première surcharge est utilisée pour les objets uniques, la deuxième surcharge est appelée pour les tableaux, et la troisième surcharge vous empêche de spécifier une taille de tableau dans l’argument de type (make_unique\<T[N]>) ; cette construction n’est pas prise en charge par la norme actuelle. Quand vous utilisez `make_unique` pour créer un `unique_ptr` dans un tableau, vous devez initialiser les éléments du tableau séparément. Si vous envisagez d’utiliser cette surcharge, un meilleur choix peut consister à utiliser un [std::vector](../standard-library/vector-class.md).

`make_unique` étant implémentée soigneusement pour la protection contre les exceptions, nous vous recommandons d’utiliser `make_unique` au lieu d’appeler directement des constructeurs `unique_ptr`.

### <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser `make_unique`. Pour obtenir plus d’exemples, consultez [Guide pratique pour créer et utiliser des instances unique_ptr](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Quand vous voyez l’erreur C2280 en lien avec `unique_ptr`, il est presque certain que vous essayez d’appeler son constructeur de recopie, qui est une fonction supprimée.

## <a name="owner_less"></a>  owner_less

Permet des comparaisons mixtes basées sur la propriété de pointeurs partagés et faibles. Retourne `true` si le paramètre de gauche est ajouté avant le paramètre de droite par la fonction membre `owner_before`.

```cpp
template <class Type>
struct owner_less; // not defined

template <class Type>
struct owner_less<shared_ptr<Type>> {
    bool operator()(
    const shared_ptr<Type>& left,
    const shared_ptr<Type>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Type>& right);
};

template <class Type>
struct owner_less<weak_ptr<Type>>
    bool operator()(
    const weak_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Ty>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);
};
```

### <a name="parameters"></a>Paramètres

`_left` Pointeur partagé ou faible.

`right` Pointeur partagé ou faible.

### <a name="remarks"></a>Notes

Les classes de modèle définissent tous leurs opérateurs membres comme retournant `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a>  return_temporary_buffer

Libère la mémoire temporaire allouée à l'aide de la fonction de modèle `get_temporary_buffer`.

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Paramètres

*_Pbuf* un pointeur vers la mémoire à libérer.

### <a name="remarks"></a>Notes

Cette fonction doit être utilisée uniquement pour la mémoire temporaire.

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
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300 };
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
   return_temporary_buffer ( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
 could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>  static_pointer_cast

Cast statique en shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Paramètres

`Ty` Type contrôlé par le pointeur partagé retourné.

`Other` Type contrôlé par le pointeur partagé d’argument.

`Other` Pointeur partagé d’argument.

### <a name="remarks"></a>Notes

La fonction de modèle retourne un objet shared_ptr vide si `sp` est vide `shared_ptr` objet ; sinon, elle retourne un [shared_ptr, classe](../standard-library/shared-ptr-class.md)\<Ty > objet qui détient la ressource appartenant à `sp`. L'expression `static_cast<Ty*>(sp.get())` doit être valide.

### <a name="example"></a>Exemple

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
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

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="swap"></a>  swap (Bibliothèque standard C++)

Remplacer deux objets shared_ptr ou weak_ptr.

```cpp
template <class Ty, class Other>
void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Paramètres

`Ty` Type contrôlé par le pointeur partagé/faible de gauche.

`Other` Type contrôlé par le pointeur partagé/faible de droite.

`left` Le pointeur partagé/faible de gauche.

`right` Le pointeur partagé/faible de droite.

### <a name="remarks"></a>Notes

Les fonctions de modèle appellent `left.swap(right)`.

### <a name="example"></a>Exemple

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

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

## <a name="undeclare_no_pointers"></a>  undeclare_no_pointers

Informe un récupérateur de mémoire que les caractères dans le bloc de mémoire défini par un pointeur d'adresse de base et une taille de bloc peuvent maintenant contenir des pointeurs traçables.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="remarks"></a>Notes

La fonction informe un RÉCUPÉRATEUR de mémoire que la plage d’adresses `[ptr, ptr + _Size)` peuvent maintenant contenir des pointeurs traçables.

## <a name="undeclare_reachable"></a>  undeclare_reachable

Révoque une déclaration de l’accessibilité d’un emplacement mémoire spécifié.

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`ptr`|Pointeur vers l’adresse mémoire devant être déclarée comme non accessible.|

### <a name="remarks"></a>Notes

Si `ptr` n’est pas `nullptr`, la fonction informe un RÉCUPÉRATEUR de mémoire qui `ptr` n’est plus accessible. Il retourne un pointeur en toute sécurité dérivée qui compare égal à `ptr`.

## <a name="uninitialized_copy"></a>  uninitialized_copy

Copie les objets d'une plage source spécifiée dans une plage de destination non initialisée.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Paramètres

`first` Itérateur d’entrée ciblant le premier élément dans la plage source.

`last` Itérateur d’entrée ciblant le dernier élément dans la plage source.

`dest` Un itérateur forward qui traite le premier élément dans la plage de destination.

### <a name="return-value"></a>Valeur de retour

Un itérateur vers l’avant ciblant la première position au-delà de la plage de destination, à moins que la plage source est vide.

### <a name="remarks"></a>Notes

Cet algorithme permet de découpler l'allocation de mémoire et la construction d'objet.

La fonction de modèle est exécutée :

```cpp
while (first != last) {
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

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
    Integer(int x) : val(x) {}
    int get() { return val; }
private:
    int val;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    int i;
    cout << "The initialized Array contains " << N << " elements: ";
    for (i = 0; i < N; i++)
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

## <a name="uninitialized_copy_n"></a>  uninitialized_copy_n

Crée une copie d'un nombre spécifié d'éléments à partir d'un itérateur d'entrée. Les copies sont placées dans un itérateur vers l’avant.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Paramètres

`first` Itérateur d’entrée qui fait référence à l’objet à copier.

`count` Un type entier signé ou non signé spécifiant le nombre de fois pour copier l’objet.

`dest` Itérateur vers l’avant qui fait référence à où obtenir de nouvelles copies.

### <a name="return-value"></a>Valeur de retour

Itérateur vers l’avant qui traite la première position au-delà de la destination. Si la plage source est vide, l’itérateur adresses `first`.

### <a name="remarks"></a>Notes

La fonction de modèle effectue les opérations suivantes :

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

## <a name="uninitialized_fill"></a>  uninitialized_fill

Copie les objets d'une valeur spécifiée dans une plage de destination non initialisée.

```cpp
template <class ForwardIterator, class Type>
void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Paramètres

`first` Un itérateur forward qui traite le premier élément dans la plage de destination qui doit être lancée.

`last` Un itérateur forward qui traite le dernier élément dans la plage de destination qui doit être lancée.

`val` La valeur à utiliser pour initialiser la plage de destination.

### <a name="remarks"></a>Notes

Cet algorithme permet de découpler l'allocation de mémoire et la construction d'objet.

La fonction de modèle est exécutée :

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (val);
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

### <a name="example"></a>Exemple

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer {         // No default constructor
   public:
      Integer( int x ) : val( x ) {}
      int get( ) { return val; }
   private:
      int val;
};

int main( )
{
   const int N = 10;
   Integer val ( 25 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill( Array, Array + N, val );
   int i;
   cout << "The initialized Array contains: ";
      for ( i = 0 ; i < N; i++ )
      {
         cout << Array [ i ].get( ) << " ";
      }
   cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>  uninitialized_fill_n

Copie les objets d'une valeur spécifiée dans un nombre spécifié d'éléments d'une plage de destination non initialisée.

```cpp
template <class FwdIt, class Size, class Type>
void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>Paramètres

`first` Un itérateur forward qui traite le premier élément dans la plage de destination soit lancé.

`count` Le nombre d’éléments à initialiser.

`val` La valeur à utiliser pour initialiser la plage de destination.

### <a name="remarks"></a>Notes

Cet algorithme permet de découpler l'allocation de mémoire et la construction d'objet.

La fonction de modèle est exécutée :

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(val);
```

à moins que le code ne provoque la levée d'une exception. Dans ce cas, tous les objets construits sont détruits et l’exception est de nouveau levée.

### <a name="example"></a>Exemple

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer {   // No default constructor
public:
   Integer( int x ) : val( x ) {}
   int get( ) { return val; }
private:
   int val;
};

int main() {
   const int N = 10;
   Integer val ( 60 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill_n( Array, N, val );  // C4996
   int i;
   cout << "The uninitialized Array contains: ";
   for ( i = 0 ; i < N; i++ )
      cout << Array [ i ].get( ) <<  " ";
}
```

## <a name="see-also"></a>Voir aussi

[\<memory>](../standard-library/memory.md)<br/>
