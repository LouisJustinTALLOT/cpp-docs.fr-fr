---
title: 'Pointeur :::no-loc(this):::'
description: 'Le :::no-loc(this)::: pointeur est un pointeur généré par le compilateur vers l’objet actuel dans des fonctions membres non statiques.'
ms.date: 01/22/2020
f1_keywords:
- :::no-loc(this):::_cpp
helpviewer_keywords:
- nonstatic member functions [C++]
- 'pointers, to :::no-loc(class)::: instance'
- ':::no-loc(this)::: pointer'
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
no-loc:
- ':::no-loc(this):::'
- ':::no-loc(class):::'
- ':::no-loc(struct):::'
- ':::no-loc(union):::'
- ':::no-loc(sizeof):::'
- ':::no-loc(const):::'
- ':::no-loc(volatile):::'
ms.openlocfilehash: c851beaba7fe1091ffd7827714f90307303058c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225824"
---
# <a name="no-locthis-pointer"></a>Pointeur :::no-loc(this):::

Le **`:::no-loc(this):::`** pointeur est un pointeur accessible uniquement dans les fonctions membres non statiques d' **`:::no-loc(class):::`** un **`:::no-loc(struct):::`** type, ou **`:::no-loc(union):::`** . Il pointe vers l'objet pour lequel la fonction membre est appelée. Les fonctions membres statiques n’ont pas de **`:::no-loc(this):::`** pointeur.

## <a name="syntax"></a>Syntaxe

```cpp
:::no-loc(this):::
:::no-loc(this):::->member-identifier
```

## <a name="remarks"></a>Notes

Le pointeur d’un objet **`:::no-loc(this):::`** ne fait pas partie de l’objet lui-même. Elle n’est pas reflétée dans le résultat d’une **`:::no-loc(sizeof):::`** instruction sur l’objet. Lorsqu’une fonction membre non statique est appelée pour un objet, le compilateur passe l’adresse de l’objet à la fonction en tant qu’argument masqué. Par exemple, l'appel de fonction suivant :

```cpp
myDate.setMonth( 3 );
```

peut être interprété comme suit :

```cpp
setMonth( &myDate, 3 );
```

L’adresse de l’objet est disponible dans la fonction membre en tant que **`:::no-loc(this):::`** pointeur. La plupart des **`:::no-loc(this):::`** utilisations de pointeur sont implicites. Il est légal, bien que inutile, d’utiliser un Explicit pour faire **`:::no-loc(this):::`** référence aux membres de :::no-loc(class)::: . Par exemple :

```cpp
void Date::setMonth( int mn )
{
   month = mn;            // These three statements
   :::no-loc(this):::->month = mn;      // are equivalent
   (*:::no-loc(this):::).month = mn;
}
```

L’expression **`*:::no-loc(this):::`** est couramment utilisée pour retourner l’objet actuel à partir d’une fonction membre :

```cpp
return *:::no-loc(this):::;
```

Le **`:::no-loc(this):::`** pointeur est également utilisé pour assurer la protection contre les auto-références :

```cpp
if (&Object != :::no-loc(this):::) {
// do not execute in cases of self-reference
```

> [!NOTE]
> Étant donné que le **`:::no-loc(this):::`** pointeur n’est pas modifiable, les assignations au **`:::no-loc(this):::`** pointeur ne sont pas autorisées. Les implémentations antérieures de C++ permettaient l’assignation à **`:::no-loc(this):::`** .

Parfois, le **`:::no-loc(this):::`** pointeur est utilisé directement, par exemple pour manipuler les données auto-référentielles :::no-loc(struct)::: ures, où l’adresse de l’objet actuel est requise.

## <a name="example"></a>Exemple

```cpp
// :::no-loc(this):::_pointer.cpp
// compile with: /EHsc

#include <iostream>
#include <string.h>

using namespace std;

:::no-loc(class)::: Buf
{
public:
    Buf( char* szBuffer, size_t sizeOfBuffer );
    Buf& operator=( :::no-loc(const)::: Buf & );
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

Buf& Buf::operator=( :::no-loc(const)::: Buf &otherbuf )
{
    if( &otherbuf != :::no-loc(this)::: )
    {
        if (buffer)
            delete [] buffer;

        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;
        buffer = new char[sizeOfBuffer];
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );
    }
    return *:::no-loc(this):::;
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

## <a name="type-of-the-no-locthis-pointer"></a>Type du :::no-loc(this)::: pointeur

Le **`:::no-loc(this):::`** type du pointeur peut être modifié dans la déclaration de fonction par **`:::no-loc(const):::`** les **`:::no-loc(volatile):::`** Mots clés et. Pour déclarer une fonction qui a l’un de ces attributs, ajoutez le ou les mots clés après la liste d’arguments de la fonction.

Prenons un exemple :

```cpp
// type_of_:::no-loc(this):::_pointer1.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

Le code précédent déclare une fonction membre, `X` , dans laquelle le **`:::no-loc(this):::`** pointeur est traité comme un **`:::no-loc(const):::`** pointeur vers un **`:::no-loc(const):::`** objet. Des combinaisons d’options *CV-mod-List* peuvent être utilisées, mais elles modifient toujours l’objet vers lequel pointe le **`:::no-loc(this):::`** pointeur, pas le pointeur lui-même. La déclaration suivante déclare la fonction `X` , où le **`:::no-loc(this):::`** pointeur est un **`:::no-loc(const):::`** pointeur vers un **`:::no-loc(const):::`** objet :

```cpp
// type_of_:::no-loc(this):::_pointer2.cpp
:::no-loc(class)::: Point
{
    unsigned X() :::no-loc(const):::;
};
int main()
{
}
```

Le type de **`:::no-loc(this):::`** dans une fonction membre est décrit par la syntaxe suivante. La *liste CV-qualifier* est déterminée à partir du déclarateur de la fonction membre. Il peut être **`:::no-loc(const):::`** ou **`:::no-loc(volatile):::`** (ou les deux). * :::no-loc(class)::: -type* est le nom du :::no-loc(class)::: :

[*CV-qualifier-List*] * :::no-loc(class)::: -type* ** \* :::no-loc(const)::: :::no-loc(this)::: **

En d’autres termes, le **`:::no-loc(this):::`** pointeur est toujours un :::no-loc(const)::: pointeur. Il ne peut pas être réassigné.  Les **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** qualificateurs ou utilisés dans la déclaration de fonction membre s’appliquent à l' :::no-loc(class)::: instance vers **`:::no-loc(this):::`** laquelle pointe le pointeur, dans la portée de cette fonction.

Le tableau ci-dessous fournit davantage d'explications sur le fonctionnement de ces modificateurs.

### <a name="semantics-of-no-locthis-modifiers"></a>Sémantique des :::no-loc(this)::: modificateurs

|Modificateur|Signification|
|--------------|-------------|
|**`:::no-loc(const):::`**|Impossible de modifier les données de membre ; Impossible d’appeler des fonctions membres qui ne le sont pas **`:::no-loc(const):::`** .|
|**`:::no-loc(volatile):::`**|Les données de membre sont chargées à partir de la mémoire chaque fois que vous y accédez ; désactive certaines optimisations.|

C’est une erreur de passer un **`:::no-loc(const):::`** objet à une fonction membre qui n’est pas **`:::no-loc(const):::`** .

De même, il s’agit également d’une erreur pour passer un **`:::no-loc(volatile):::`** objet à une fonction membre qui n’est pas **`:::no-loc(volatile):::`** .

Les fonctions membres déclarées comme **`:::no-loc(const):::`** ne peuvent pas modifier les données de membre — dans ces fonctions, le **`:::no-loc(this):::`** pointeur est un pointeur vers un **`:::no-loc(const):::`** objet.

> [!NOTE]
> Les con :::no-loc(struct)::: ors et les :::no-loc(struct)::: ors ne peuvent pas être déclarés en tant que **`:::no-loc(const):::`** ou **`:::no-loc(volatile):::`** . Toutefois, elles peuvent être appelées sur des **`:::no-loc(const):::`** **`:::no-loc(volatile):::`** objets ou.

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
