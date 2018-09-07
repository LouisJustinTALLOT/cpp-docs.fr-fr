---
title: '&lt;new&gt;, opérateurs | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
author: corob-msft
ms.author: corob
ms.openlocfilehash: 31db26453efbecceb136b614b8eabf178a0cdfea
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100364"
---
# <a name="ltnewgt-operators"></a>&lt;new&gt;, opérateurs

||||
|-|-|-|
|[operator delete](#op_delete)|[operator delete[]](#op_delete_arr)|[operator new](#op_new)|
|[operator new[]](#op_new_arr)|

## <a name="op_delete"></a>  operator delete

Fonction appelée par une expression delete pour libérer le stockage pour des objets distincts.

```cpp
void operator delete(void* ptr) throw();

void operator delete(void *,
    void*) throw();

void operator delete(void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Pointeur dont la valeur doit être rendue non valide par la suppression.

### <a name="remarks"></a>Notes

La première fonction est appelée par une expression delete pour rendre la valeur de *ptr* non valide. Le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++. Le comportement exigé consiste à accepter une valeur de *ptr* qui est null ou qui a été retournée par un appel antérieur à [opérateur new](../standard-library/new-operators.md#op_new)(**size_t**).

Le comportement par défaut d’une valeur null de *ptr* consiste à ne rien faire. Toute autre valeur de *ptr* doit être une valeur retournée précédemment par un appel comme décrit précédemment. Le comportement par défaut pour ce type d’une valeur non null de *ptr* consiste à récupérer le stockage alloué par l’appel précédent. Il n’est pas spécifié dans quelles conditions tout ou partie de ce stockage récupéré est alloué par un appel ultérieur à `operator new`(**size_t**), ou à une des `calloc`( **size_t**), `malloc`( **size_t**), ou `realloc`( **void**<strong>\*</strong>, **size_t**).

La deuxième fonction est appelée par une expression delete de positionnement correspondant à une expression de la forme **new**( **std::size_t**). Elle ne fait rien.

La troisième fonction est appelée par une expression delete de positionnement correspondant à une expression new de la forme **new**( **std::size_t**, **conststd::nothrow_t&**). Le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++. Le comportement exigé consiste à accepter une valeur de `ptr` qui est Null ou qui a été retournée par un appel précédent à `operator new`( **size_t**). Le comportement par défaut consiste à évaluer **supprimer**(`ptr`).

### <a name="example"></a>Exemple

Consultez [opérateur new](../standard-library/new-operators.md#op_new) pour obtenir un exemple qui utilisent **opérateur delete**.

## <a name="op_delete_arr"></a>  operator delete[]

Fonction appelée par une expression delete pour libérer le stockage pour un tableau d'objets.

```cpp
void operator delete[](void* ptr) throw();

void operator delete[](void *,
    void*) throw();

void operator delete[](void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Paramètres

*ptr*<br/>
Pointeur dont la valeur doit être rendue non valide par la suppression.

### <a name="remarks"></a>Notes

La première fonction est appelée par un `delete[]` expression pour rendre la valeur de *ptr* non valide. La fonction est remplaçable, car le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++. Le comportement exigé consiste à accepter une valeur de *ptr* qui est null ou qui a été retournée par un appel antérieur à [opérateur new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)(**size_t**). Le comportement par défaut d’une valeur null de *ptr* consiste à ne rien faire. Toute autre valeur de *ptr* doit être une valeur retournée précédemment par un appel comme décrit précédemment. Le comportement par défaut pour ce type d’une valeur non null de *ptr* consiste à récupérer le stockage alloué par l’appel précédent. Il n’est pas spécifié dans quelles conditions tout ou partie de ce stockage récupéré est alloué par un appel ultérieur à [opérateur new](../standard-library/new-operators.md#op_new)(**size_t**), ou à une des `calloc`(**size_t**), `malloc`(**size_t**), ou `realloc`( **void**<strong>\*</strong>, **size_t**) .

La deuxième fonction est appelée par un positionnement `delete[]` expression correspondant à un `new[]` expression sous la forme `new[]`(**std::size_t**). Elle ne fait rien.

La troisième fonction est appelée par une expression delete de positionnement correspondant à une expression `new[]` de la forme `new[]`( **std::size_t**, **const std::nothrow_t&**). Le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++. Le comportement exigé consiste à accepter une valeur de *ptr* qui est null ou qui a été retournée par un appel précédent à l’opérateur `new[]`(**size_t**). Le comportement par défaut consiste à évaluer `delete[]`( `ptr`).

### <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de `operator delete[]`, consultez [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr).

## <a name="op_new"></a>  operator new

Fonction appelée par une expression new pour allouer le stockage pour des objets distincts.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);

void* operator new(std::size_t count,
    const std::nothrow_t&) throw();

void* operator new(std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre d’octets de stockage à allouer.

*ptr*<br/>
Pointeur à retourner.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’adresse de poids le plus faible de la mémoire nouvellement allouée. Ou *ptr*.

### <a name="remarks"></a>Notes

La première fonction est appelée par une expression new pour allouer `count` octets de stockage alignés correctement pour représenter tout objet de cette taille. La fonction est remplaçable, car le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++.

Le comportement exigé consiste à retourner un pointeur non Null uniquement si le stockage peut être alloué comme demandé. Chaque allocation génère un pointeur vers du stockage disjoint de tout autre stockage alloué. L’ordre et la contiguïté du stockage alloué par les appels successifs ne sont pas spécifiés. La valeur stockée initiale n’est pas spécifiée. Le pointeur retourné pointe vers le début (adresse de poids le plus faible) du stockage alloué. Si le décompte est égal à zéro, la valeur retournée est considérée comme n’étant égale à aucune autre valeur retournée par la fonction.

Le comportement par défaut consiste à exécuter une boucle. Dans la boucle, la fonction tente d’abord d’allouer le stockage demandé. Le fait que la tentative implique ou non un appel à `malloc`( **size_t**) n’est pas spécifié. Si la tentative réussit, la fonction retourne un pointeur vers le stockage alloué. Sinon, la fonction appelle le [gestionnaire new](../standard-library/new-typedefs.md#new_handler) désigné. Si la fonction appelée retourne, la boucle se répète. La boucle se termine quand une tentative d’allocation de stockage demandée réussit ou quand une fonction appelée ne retourne pas.

Le comportement exigé d’un gestionnaire new consiste à effectuer l’une des opérations suivantes :

- Rendre plus de stockage disponible pour l’allocation, puis retourner.

- Appelez **abandonner** ou **quitter**(`int`).

- Lever un objet de type **bad_alloc**.

Le comportement par défaut d’un [gestionnaire new](../standard-library/new-typedefs.md#new_handler) consiste à lever un objet de type `bad_alloc`. Un pointeur Null désigne le gestionnaire new par défaut.

L’ordre et la contiguïté du stockage alloué par les appels successifs à `operator new`(**size_t**) n’est pas spécifié, comme le sont les valeurs initiales qui y sont stockés.

La deuxième fonction est appelée par une expression new de positionnement pour allouer `count` octets de stockage alignés correctement pour représenter tout objet de cette taille. La fonction est remplaçable, car le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++.

Le comportement par défaut consiste à retourner `operator new`(`count`) si cette fonction réussit. Sinon, elle retourne un pointeur Null.

La troisième fonction est appelée par une expression **new** de positionnement, de la forme **new** ( *args*) T. Ici, *args* se compose d’un pointeur d’objet unique. Cela peut être utile pour construire un objet à une adresse connue. La fonction retourne *ptr*.

Pour libérer le stockage alloué par **opérateur new**, appelez [opérateur delete](../standard-library/new-operators.md#op_delete).

Pour plus d’informations sur le comportement de levée de new, consultez [Opérateurs new et delete](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Exemple

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a>  operator new[]

Fonction d’allocation appelée par une expression new pour allouer le stockage pour un tableau d’objets.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);

void* operator new[](std::size_t count,
    const std::nothrow_t&) throw();

void* operator new[](std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Paramètres

*count*<br/>
Nombre d’octets de stockage à allouer pour l’objet tableau.

*ptr*<br/>
Pointeur à retourner.

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’adresse de poids le plus faible de la mémoire nouvellement allouée. Ou *ptr*.

### <a name="remarks"></a>Notes

La première fonction est appelée par une expression `new[]` pour allouer `count` octets de stockage alignés correctement pour représenter tout objet de tableau de cette taille ou plus petit. Le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++. Le comportement exigé est identique à celle de [opérateur new](../standard-library/new-operators.md#op_new)(**size_t**). Le comportement par défaut consiste à retourner `operator new`( `count`).

La deuxième fonction est appelée par une expression `new[]` de positionnement pour allouer `count` octets de stockage alignés correctement pour représenter tout objet de tableau de cette taille. Le programme peut définir une fonction avec cette signature de fonction qui remplace la version par défaut définie par la bibliothèque standard C++. Le comportement par défaut consiste à retourner **operatornew**(`count`) si cette fonction réussit. Sinon, elle retourne un pointeur Null.

La troisième fonction est appelée par une expression `new[]` de positionnement, de la forme **new** ( *args*) **T**[ **N**]. Ici, *args* se compose d’un pointeur d’objet unique. La fonction retourne `ptr`.

Pour libérer le stockage alloué par `operator new[]`, appelez [operator delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr).

Pour plus d’informations sur le comportement de levée de new, consultez [Opérateurs new et delete](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Exemple

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```

## <a name="see-also"></a>Voir aussi

[\<new>](../standard-library/new.md)<br/>
