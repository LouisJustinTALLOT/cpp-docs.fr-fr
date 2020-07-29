---
title: Pointeurs bruts (C++)
description: Comment utiliser des pointeurs bruts en C++
ms.date: 04/21/2020
helpviewer_keywords:
- pointers [C++]
no-loc:
- ':::no-loc(void):::'
- ':::no-loc(nullptr):::'
- ':::no-loc(const):::'
- ':::no-loc(char):::'
- ':::no-loc(new):::'
- ':::no-loc(delete):::'
ms.openlocfilehash: 53679559888191fe7f2aad7cb5a70d607974ae96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233650"
---
# <a name="raw-pointers-c"></a>Pointeurs bruts (C++)

Un *pointeur* est un type de variable. Elle stocke l’adresse d’un objet en mémoire et est utilisée pour accéder à cet objet. Un *pointeur brut* est un pointeur dont la durée de vie n’est pas contrôlée par un objet d’encapsulation, tel qu’un [pointeur intelligent](smart-pointers-modern-cpp.md). Un pointeur brut peut se voir assigner l’adresse d’une autre variable qui n’est pas un pointeur, ou une valeur peut lui être assignée [:::no-loc(nullptr):::](:::no-loc(nullptr):::.md) . Un pointeur auquel aucune valeur n’a été assignée contient des données aléatoires.

Un pointeur peut également être *déréférencé* pour récupérer la valeur de l’objet vers lequel il pointe. L' *opérateur d’accès aux membres* fournit l’accès aux membres d’un objet.

```cpp
    int* p = :::no-loc(nullptr):::; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address
```

Un pointeur peut pointer vers un objet typé ou vers **`:::no-loc(void):::`** . Lorsqu’un programme alloue un objet sur le [tas](https://wikipedia.org/wiki/Heap) en mémoire, il reçoit l’adresse de cet objet sous la forme d’un pointeur. Ces pointeurs sont appelés *pointeurs propriétaires*. Un pointeur propriétaire (ou une copie de celui-ci) doit être utilisé pour libérer explicitement l’objet alloué au tas lorsqu’il n’est plus nécessaire. Si vous ne libérez pas la mémoire, une *fuite*de mémoire se produit et le rendu de cet emplacement mémoire n’est pas disponible pour les autres programmes sur l’ordinateur. La mémoire allouée à l’aide **`:::no-loc(new):::`** de doit être libérée à l’aide **`:::no-loc(delete):::`** de (ou ** :::no-loc(delete)::: \[ ]**). Pour plus d’informations, consultez [ :::no-loc(new)::: :::no-loc(delete)::: opérateurs et](:::no-loc(new):::-and-:::no-loc(delete):::-operators.md).

```cpp
    MyClass* mc = :::no-loc(new)::: MyClass(); // allocate object on the heap
    mc->print(); // access class member
    :::no-loc(delete)::: mc; // :::no-loc(delete)::: object (please don't forget!)
```

Un pointeur (s’il n’est pas déclaré comme **`:::no-loc(const):::`** ) peut être incrémenté ou décrémenté pour pointer vers un autre emplacement dans la mémoire. Cette opération est appelée *arithmétique de pointeur*. Elle est utilisée dans la programmation de style C pour itérer au sein des éléments dans des tableaux ou d’autres structures de données. Un **`:::no-loc(const):::`** pointeur ne peut pas être créé pour pointer vers un emplacement de mémoire différent et, dans ce sens, est similaire à une [référence](references-cpp.md). Pour plus d’informations, consultez [ :::no-loc(const)::: et pointeurs volatiles](:::no-loc(const):::-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    :::no-loc(const)::: :::no-loc(char):::* str = "Hello world";

    :::no-loc(const)::: int c = 1;
    :::no-loc(const)::: int* p:::no-loc(const)::: = &c; // declare a non-:::no-loc(const)::: pointer to :::no-loc(const)::: int
    :::no-loc(const)::: int c2 = 2;
    p:::no-loc(const)::: = &c2;  // OK p:::no-loc(const)::: itself isn't :::no-loc(const):::
    :::no-loc(const)::: int* :::no-loc(const)::: p:::no-loc(const):::2 = &c;
    // p:::no-loc(const):::2 = &c2; // Error! p:::no-loc(const):::2 is :::no-loc(const):::.
```

Sur les systèmes d’exploitation 64 bits, un pointeur a une taille de 64 bits. La taille du pointeur du système détermine la quantité de mémoire adressable qu’il peut avoir. Toutes les copies d’un pointeur pointent vers le même emplacement de mémoire. Les pointeurs (ainsi que les références) sont utilisés de manière intensive en C++ pour passer des objets plus grands à des fonctions et à partir de celles-ci. C’est parce qu’il est souvent plus efficace de copier l’adresse d’un objet que de copier l’objet entier. Lors de la définition d’une fonction, spécifiez des paramètres de pointeur comme **`:::no-loc(const):::`** si vous souhaitiez que la fonction modifie l’objet. En général, les **`:::no-loc(const):::`** références sont le meilleur moyen de passer des objets aux fonctions, sauf si la valeur de l’objet peut être **`:::no-loc(nullptr):::`** .

Les [pointeurs vers des fonctions](#pointers_to_functions) permettent de passer des fonctions à d’autres fonctions et sont utilisées pour les « rappels » dans la programmation de style C. Le C++ moderne utilise des [expressions lambda](lambda-expressions-in-cpp.md) à cet effet.

## <a name="initialization-and-member-access"></a>Initialisation et accès aux membres

L’exemple suivant montre comment déclarer, initialiser et utiliser un pointeur brut. Elle est initialisée à l’aide **`:::no-loc(new):::`** de pour pointer un objet alloué sur le tas, ce que vous devez explicitement **`:::no-loc(delete):::`** . L’exemple montre également quelques-uns des dangers associés aux pointeurs bruts. (N’oubliez pas que cet exemple concerne la programmation de style C et non le C++ moderne)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
:::no-loc(void)::: func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
:::no-loc(void)::: func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use :::no-loc(new)::: to allocate and initialize memory
    MyClass* pmc = :::no-loc(new)::: MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(pmc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*pmc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    :::no-loc(delete):::(pmc); // don't forget to give memory back to operating system!
   // :::no-loc(delete):::(pmc2); //crash! memory location was already :::no-loc(delete):::d
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Opérations arithmétiques sur les pointeurs et tableaux

Les pointeurs et les tableaux sont étroitement liés. Lorsqu’un tableau est passé par valeur à une fonction, il est passé en tant que pointeur vers le premier élément. L’exemple suivant illustre les propriétés importantes suivantes des pointeurs et des tableaux :

- l' **`sizeof`** opérateur retourne la taille totale en octets d’un tableau
- pour déterminer le nombre d’éléments, diviser le total des octets par la taille d’un élément
- Lorsqu’un tableau est passé à une fonction, il s' *atténue* à un type pointeur
- l' **`sizeof`** opérateur appliqué à un pointeur retourne la taille du pointeur, 4 octets sur x86 ou 8 octets sur x64

```cpp
#include <iostream>

:::no-loc(void)::: func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

Certaines opérations arithmétiques peuvent être utilisées sur des non- :::no-loc(const)::: pointeurs pour les faire pointer vers un autre emplacement de mémoire. Les pointeurs sont incrémentés et décrémenté à l’aide des **++** **+=** opérateurs, **-=** et **--** . Cette technique peut être utilisée dans les tableaux et est particulièrement utile dans les tampons de données non typées. Un **:::no-loc(void):::\*** est incrémenté par la taille d’un **`:::no-loc(char):::`** (1 octet). Un pointeur typé est incrémenté par taille du type vers lequel il pointe.

L’exemple suivant montre comment les opérations arithmétiques sur les pointeurs peuvent être utilisées pour accéder à des pixels individuels dans une image bitmap sur Windows. Notez l’utilisation de et de et de **`:::no-loc(new):::`** **`:::no-loc(delete):::`** l’opérateur de déréférencement.

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    :::no-loc(const):::expr int bufferSize = 30000;
    unsigned :::no-loc(char):::* buffer = :::no-loc(new)::: unsigned :::no-loc(char):::[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned :::no-loc(char):::* begin = &buffer[0];
    unsigned :::no-loc(char):::* end = &buffer[0] + bufferSize;
    unsigned :::no-loc(char):::* p = begin;
    :::no-loc(const):::expr int pixelWidth = 3;
    :::no-loc(const):::expr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned :::no-loc(char):::).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<:::no-loc(char):::*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(&header), sizeof(header));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(begin), bufferSize);

    :::no-loc(delete):::[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="no-locvoid-pointers"></a>:::no-loc(void):::* pointeurs

Un pointeur vers **`:::no-loc(void):::`** pointe simplement vers un emplacement de mémoire brut. Il est parfois nécessaire d’utiliser **:::no-loc(void):::\*** des pointeurs, par exemple lors du passage entre du code C++ et des fonctions C.

Quand un pointeur typé est casté en :::no-loc(void)::: pointeur, le contenu de l’emplacement de mémoire n’est pas modifié. Toutefois, les informations de type sont perdues, ce qui vous évitera d’effectuer des opérations d’incrémentation ou de décrémentation. Un emplacement de mémoire peut être casté, par exemple, de `MyClass*` vers, **`:::no-loc(void):::*`** puis de nouveau vers `MyClass*` . Ces opérations sont par nature sujettes aux erreurs et nécessitent une attention particulière aux :::no-loc(void)::: Erreurs. Le C++ moderne déconseille l’utilisation de :::no-loc(void)::: pointeurs dans presque tous les cas.

```cpp

//func.c
:::no-loc(void)::: func(:::no-loc(void):::* data, int length)
{
    :::no-loc(char):::* c = (:::no-loc(char):::*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    :::no-loc(void)::: func(:::no-loc(void):::* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = :::no-loc(new)::: MyClass{10, "Marian"};
    :::no-loc(void):::* p = static_cast<:::no-loc(void):::*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator :::no-loc(new)::: to allocate untyped memory block
    :::no-loc(void):::* p:::no-loc(void)::: = operator :::no-loc(new):::(1000);
    :::no-loc(char):::* p:::no-loc(char)::: = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::);
    for(:::no-loc(char):::* c = p:::no-loc(char):::; c < p:::no-loc(char)::: + 1000; ++c)
    {
        *c = 0x00;
    }
    func(p:::no-loc(void):::, 1000);
    :::no-loc(char)::: ch = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::)[0];
    std::cout << ch << std::endl; // 'A'
    operator :::no-loc(delete):::(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Pointeurs vers des fonctions

Dans la programmation de style C, les pointeurs de fonction sont utilisés principalement pour passer des fonctions à d’autres fonctions. Cette technique permet à l’appelant de personnaliser le comportement d’une fonction sans la modifier. Dans le C++ moderne, les [expressions lambda](lambda-expressions-in-cpp.md) fournissent la même fonctionnalité avec une sécurité de type supérieure et d’autres avantages.

Une déclaration de pointeur de fonction spécifie la signature que la fonction pointant doit avoir :

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
:::no-loc(void)::: (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

L’exemple suivant montre une fonction `combine` qui prend comme paramètre toute fonction qui accepte un `std::string` et retourne un `std::string` . Selon la fonction qui est passée à `combine` , il ajoute ou ajoute une chaîne.

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>Voir aussi

[Pointeurs intelligents](smart-pointers-modern-cpp.md) 
 [Opérateur d’indirection : *](indirection-operator-star.md)<br/>
[address-of, opérateur](address-of-operator-amp.md)</br>
[Bienvenue dans C++](welcome-back-to-cpp-modern-cpp.md)
