---
title: Pointeur this
description: Le pointeur this est un pointeur généré par le compilateur vers l’objet actuel dans des fonctions membres non statiques.
ms.date: 01/22/2020
f1_keywords:
- this_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- this
- class
- struct
- union
- sizeof
- const
- volatile
ms.openlocfilehash: 58bba2edd7a457c624b747b5a65d209995852848
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518333"
---
# <a name="opno-locthis-pointer"></a>Pointeur this

Le pointeur **this** est un pointeur accessible uniquement dans les fonctions membres non statiques d’un type **class** , **struct** ou **union** . Il pointe vers l'objet pour lequel la fonction membre est appelée. Les fonctions membres statiques n’ont pas de pointeur **this** .

## <a name="syntax"></a>Syntaxe

```cpp
this
this->member-identifier
```

## <a name="remarks"></a>Notes

Le pointeur **this** d’un objet ne fait pas partie de l’objet lui-même. Elle n’est pas reflétée dans le résultat d’une instruction **sizeof** sur l’objet. Lorsqu’une fonction membre non statique est appelée pour un objet, le compilateur passe l’adresse de l’objet à la fonction en tant qu’argument masqué. Par exemple, l'appel de fonction suivant :

```cpp
myDate.setMonth( 3 );
```

peut être interprété comme suit :

```cpp
setMonth( &myDate, 3 );
```

L’adresse de l’objet est disponible dans la fonction membre comme pointeur de **this** . La plupart des utilisations des pointeurs **this** sont implicites. Il est légal, bien que inutile, d’utiliser un **this** explicite pour faire référence aux membres du class. Par exemple :

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   this->month = mn;      // are equivalent
   (*this).month = mn;
}
```

L'expression `*this` est utilisée couramment pour retourner l'objet actuel d'une fonction membre :

```cpp
return *this;
```

Le pointeur **this** est également utilisé pour assurer la protection contre les auto-références :

```cpp
if (&Object != this) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Étant donné que le pointeur **this** n’est pas modifiable, les assignations au pointeur **this** ne sont pas autorisées. Implémentations antérieures de C++ l’assignation autorisée à **this** .

Parfois, le pointeur **this** est utilisé directement, par exemple pour manipuler des structures de données auto-référentielles, où l’adresse de l’objet actuel est requise.

## <a name="example"></a>Exemple

```cpp
// this_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

class Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( const Buf & );
    void Display() { cout << buffer << endl; }

private:
    char*   buffer;
    size_t  sizeOfBuffer;
};

Buf::Buf( char* szBuffer, size_t sizeOfBuffer )
{
    sizeOfBuffer++; // account for a NULL terminator

    buffer = new char[ sizeOfBuffer ];
    if (buffer)
    {
        strcpy_s( buffer, sizeOfBuffer, szBuffer );
        sizeOfBuffer = sizeOfBuffer;
    }
}

Buf& Buf::operator=( const Buf &otherbuf )
{
    if( &otherbuf != this )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *this;
}

int main()
{
    Buf myBuf( "my buffer", 10 );
    Buf yourBuf( "your buffer", 12 );

    // Display 'my buffer'
    myBuf.Display();

    // assignment operator
    myBuf = yourBuf;

    // Display 'your buffer'
    myBuf.Display();
}
```

```Output
my buffer
your buffer
```

## <a name="type-of-the-opno-locthis-pointer"></a>Type du pointeur this

Le type du pointeur **this** peut être modifié dans la déclaration de fonction par les mots clés **const** et **volatile** . Pour déclarer une fonction qui a l’un de ces attributs, ajoutez le ou les mots clés après la liste d’arguments de la fonction.

Prenons un exemple :

```cpp
// type_of_this_pointer1.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

Le code précédent déclare une fonction membre, `X`, dans laquelle le pointeur **this** est traité comme un pointeur **const** vers un objet **const** . Des combinaisons d’options *CV-mod-List* peuvent être utilisées, mais elles modifient toujours l’objet désigné par le pointeur **this** , pas le pointeur lui-même. La déclaration suivante déclare la fonction `X`, où le pointeur **this** est un pointeur **const** vers un objet **const** :

```cpp
// type_of_this_pointer2.cpp
class Point
{
    unsigned X() const;
};
int main()
{
}
```

Le type de **this** dans une fonction membre est décrit par la syntaxe suivante. La *liste CV-qualifier* est déterminée à partir du déclarateur de la fonction membre. Il peut être **const** ou **volatile** (ou les deux). *class-type* est le nom du class:

[*CV-qualifier-List*] *class* **\* const this**

En d’autres termes, le pointeur **this** est toujours un pointeur const. Il ne peut pas être réassigné.  Les qualificateurs **const** ou **volatile** utilisés dans la déclaration de fonction membre s’appliquent à l’instance class vers laquelle pointe le pointeur **this** , dans la portée de cette fonction.

Le tableau ci-dessous fournit davantage d'explications sur le fonctionnement de ces modificateurs.

### <a name="semantics-of-opno-locthis-modifiers"></a>Sémantique des modificateurs this

|Modificateur|Signification|
|--------------|-------------|
|**const**|Impossible de modifier les données de membre ; Impossible d’appeler des fonctions membres qui ne sont pas **const** .|
|**volatile**|Les données de membre sont chargées à partir de la mémoire chaque fois que vous y accédez ; désactive certaines optimisations.|

C’est une erreur de passer un objet **const** à une fonction membre qui n’est pas **const** .

De même, il s’agit également d’une erreur pour passer un objet **volatile** à une fonction membre qui n’est pas **volatile** .

Les fonctions membres déclarées comme **const** ne peuvent pas modifier les données de membre ; dans ces fonctions, le pointeur **this** est un pointeur vers un objet **const** .

> [!NOTE]
> Les constructeurs et les destructeurs ne peuvent pas être déclarés en tant que **const** ou **volatile** . Toutefois, elles peuvent être appelées sur des objets **const** ou **volatile** .

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
