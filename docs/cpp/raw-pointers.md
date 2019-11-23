---
title: Pointeurs brutsC++()
description: Comment utiliser des pointeurs bruts dansC++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 9ea498c254bc37dc8dc550232127cb2db3bc0886
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250659"
---
# <a name="raw-pointers-c"></a>Pointeurs brutsC++()

Un pointeur est un type de variable qui stocke l’adresse d’un objet en mémoire et qui est utilisé pour accéder à cet objet. Un *pointeur brut* est un pointeur dont la durée de vie n’est pas contrôlée par un objet d’encapsulation tel qu’un [pointeur intelligent](smart-pointers-modern-cpp.md). Un pointeur brut peut se voir assigner l’adresse d’une autre variable non pointeur, ou une valeur de [nullptr](nullptr.md). Un pointeur auquel aucune valeur n’a été assignée contient des données aléatoires.

Un pointeur peut également être *déréférencé* pour récupérer la valeur de l’objet vers lequel il pointe. L' *opérateur d’accès aux membres* fournit l’accès aux membres d’un objet.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Un pointeur peut pointer vers un objet typé ou pour **Annuler**. Lorsqu’un programme alloue un nouvel objet sur le [tas](https://wikipedia.org/wiki/Heap) en mémoire, il reçoit l’adresse de cet objet sous la forme d’un pointeur. Ces pointeurs sont appelés *pointeurs propriétaires*; un pointeur propriétaire (ou une copie de celui-ci) doit être utilisé pour supprimer explicitement l’objet alloué par tas lorsqu’il n’est plus nécessaire. Si vous ne supprimez pas la mémoire, une *fuite* de mémoire se produit et le rendu de cet emplacement mémoire n’est pas disponible pour les autres programmes sur l’ordinateur. Pour plus d’informations, consultez [opérateurs New et Delete](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Un pointeur (s’il n’est pas déclaré comme **const**) peut être incrémenté ou décrémenté afin qu’il pointe vers un nouvel emplacement en mémoire. C’est ce que l’on appelle le « *arithmétique de pointeur* » et est utilisé dans la programmation de style C pour itérer au sein des éléments dans des tableaux ou d’autres structures de données. Un pointeur **const** ne peut pas être défini pour pointer vers un emplacement de mémoire différent. dans ce sens, il est très similaire à une [référence](references-cpp.md). Pour plus d’informations, consultez [pointeurs const et volatile](const-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c; 
    // pconst2 = &c2; // Error! pconst2 is const.
```

Sur les systèmes d’exploitation 64 bits, un pointeur a une taille de 64 bits ; la taille du pointeur du système détermine la quantité de mémoire adressable qu’il peut avoir. Toutes les copies d’un pointeur pointent vers le même emplacement de mémoire. Les pointeurs (ainsi que les références) sont utilisés de C++ manière intensive dans pour passer des objets plus grands à et à partir de fonctions, car il est généralement beaucoup plus efficace de copier l’adresse 64 bits d’un objet que de copier un objet entier. Lors de la définition d’une fonction, spécifiez des paramètres de pointeur comme **const** , sauf si vous envisagez de modifier l’objet par la fonction. En général, les références **const** constituent la meilleure façon de passer des objets aux fonctions, sauf si la valeur de l’objet peut être **nullptr**.

Les [pointeurs vers des fonctions](#pointers_to_functions) permettent de passer des fonctions à d’autres fonctions et sont utilisées pour les « rappels » dans la programmation de style C. Moderne C++ utilise des [expressions lambda](lambda-expressions-in-cpp.md) à cet effet.

## <a name="initialization-and-member-access"></a>Initialisation et accès aux membres

L’exemple suivant montre comment déclarer un pointeur brut et l’initialiser avec un objet alloué sur le tas, puis comment l’utiliser. Il montre également quelques-uns des dangers associés aux pointeurs bruts. (N’oubliez pas qu’il s’agit d’une programmation de C++style C et non moderne !)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
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
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

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
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Opérations arithmétiques sur les pointeurs et tableaux

Les pointeurs et les tableaux sont étroitement liés. Lorsqu’un tableau est passé par valeur à une fonction, il est passé en tant que pointeur vers le premier élément. L’exemple suivant illustre les propriétés importantes suivantes des pointeurs et des tableaux :

- l’opérateur `sizeof` retourne la taille totale en octets d’un tableau
- pour déterminer le nombre d’éléments, diviser le total des octets par la taille d’un élément
- Lorsqu’un tableau est passé à une fonction, il s' *atténue* à un type pointeur
- l’opérateur `sizeof` lorsqu’il est appliqué à un pointeur retourne la taille du pointeur, 4 octets sur x86 ou 8 octets sur x64

```cpp
#include <iostream>

void func(int arr[], int length)
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

Certaines opérations arithmétiques peuvent être effectuées sur des pointeurs non const pour qu’ils pointent vers un nouvel emplacement de mémoire. Un pointeur peut être incrémenté et décrémenté à l’aide des opérateurs **++** , **+=** , **-=** et **--** . Cette technique peut être utilisée dans les tableaux et est particulièrement utile dans les tampons de données non typées. **Void\*** incrémente de la taille d’un **caractère** (1 octet). Un pointeur typé incrémente par taille du type vers lequel il pointe.

L’exemple suivant montre comment les opérations arithmétiques sur les pointeurs peuvent être utilisées pour accéder à des pixels individuels dans une image bitmap sur Windows. Notez l’utilisation des opérateurs **New** et **Delete**, ainsi que l’opérateur de déréférencement. 

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

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

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
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>pointeurs void *

Un pointeur vers **void** pointe simplement vers un emplacement de mémoire brut. Il est parfois nécessaire d’utiliser des pointeurs de **\*void** , par exemple lors C++ de la transmission entre du code et des fonctions C. 

Quand un pointeur typé est casté en un pointeur void, le contenu de l’emplacement de mémoire n’est pas modifié, mais les informations de type sont perdues, ce qui vous permet d’effectuer des opérations d’incrémentation ou de décrémentation. Un emplacement de mémoire peut être casté, par exemple, de MyClass * à void *, puis de nouveau vers MyClass *. Ces opérations sont par nature sujettes aux erreurs et nécessitent une attention particulière pour éviter les erreurs. Moderne C++ déconseille l’utilisation de pointeurs void, sauf nécessité absolue.

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

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
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers_to_functions"></a>Pointeurs vers des fonctions

Dans la programmation de style C, les pointeurs de fonction sont utilisés principalement pour passer des fonctions à d’autres fonctions. Dans ce scénario, l’appelant peut personnaliser le comportement d’une fonction sans la modifier. Dans moderne C++, les [expressions lambda](lambda-expressions-in-cpp.md) fournissent la même fonctionnalité avec une sécurité de type supérieure et d’autres avantages.

Une déclaration de pointeur de fonction spécifie la signature que la fonction pointant doit avoir :

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

L’exemple suivant montre une fonction `combine` qui prend comme paramètre toute fonction qui accepte un `std::string` et retourne un `std::string`. Selon la fonction qui est passée à `combine` elle ajoute ou ajoute une chaîne.

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
[opérateur d’indirection : *](indirection-operator-star.md)<br/>
[address-of, opérateur](address-of-operator-amp.md)</br>
[Bienvenue dansC++](welcome-back-to-cpp-modern-cpp.md)
