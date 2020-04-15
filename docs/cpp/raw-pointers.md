---
title: Pointeurs bruts (C)
description: Comment utiliser des pointeurs bruts dans C
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 919447fcab123ce6b838391d3cc295fb8a8fe95e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374676"
---
# <a name="raw-pointers-c"></a>Pointeurs bruts (C)

Un pointeur est un type de variable qui stocke l’adresse d’un objet dans la mémoire et est utilisé pour accéder à cet objet. Un *pointeur brut* est un pointeur dont la durée de vie n’est pas contrôlée par un objet encapsulant comme un [pointeur intelligent](smart-pointers-modern-cpp.md). Un pointeur brut peut être attribué l’adresse d’une autre variable non-pointeur, ou il peut être attribué une valeur de [nullptr](nullptr.md). Un pointeur qui n’a pas été attribué une valeur contient des données aléatoires.

Un pointeur peut également être *déreféré* pour récupérer la valeur de l’objet qu’il pointe. *L’opérateur d’accès membre* donne accès aux membres d’un objet.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Un pointeur peut pointer vers **void**un objet dactylographié ou vider. Lorsqu’un programme alloue un nouvel objet sur le [tas](https://wikipedia.org/wiki/Heap) dans la mémoire, il reçoit l’adresse de cet objet sous la forme d’un pointeur. De tels pointeurs sont appelés *pointeurs de possession*; un pointeur propriétaire (ou une copie de celui-ci) doit être utilisé pour supprimer explicitement l’objet alloué au tas lorsqu’il n’est plus nécessaire. L’omission de supprimer la mémoire entraîne une *fuite de mémoire* et rend cet emplacement de mémoire indisponible à tout autre programme sur la machine. Pour plus d’informations, voir [les opérateurs nouveaux et supprimer](new-and-delete-operators.md).

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Un pointeur (s’il n’est pas déclaré comme **const**) peut être incrémenté ou décroissé de sorte qu’il indique un nouvel emplacement dans la mémoire. C’est ce qu’on appelle *l’arithmétique pointeur* et est utilisé dans la programmation de style C pour itérer sur les éléments dans les tableaux ou d’autres structures de données. Un pointeur **de cône** ne peut pas être fait pour indiquer un endroit différent de mémoire, et dans ce sens est très semblable à une [référence.](references-cpp.md) Pour plus d’informations, voir [const et pointeurs volatils](const-and-volatile-pointers.md).

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

Sur les systèmes d’exploitation 64 bits, un pointeur a une taille de 64 bits; la taille du pointeur d’un système détermine la quantité de mémoire adressable qu’il peut avoir. Toutes les copies d’un pointeur pointent vers le même emplacement de mémoire. Les pointeurs (ainsi que les références) sont largement utilisés dans le C pour passer des objets plus grands vers et depuis les fonctions, car il est généralement beaucoup plus efficace de copier l’adresse 64 bits d’un objet que de copier un objet entier. Lors de la définition d’une fonction, spécifiez les paramètres de pointeur comme **const** sauf si vous avez l’intention pour la fonction de modifier l’objet. En général, les références **de cône** sont la manière préférée de passer des objets aux fonctions à moins que la valeur de l’objet puisse éventuellement être **nulleptr**.

[Les pointeurs des fonctions](#pointers_to_functions) permettent de transmettre des fonctions à d’autres fonctions et sont utilisés pour les « rappels » dans la programmation de style C. Le Cmd moderne utilise des [expressions lambda](lambda-expressions-in-cpp.md) à cette fin.

## <a name="initialization-and-member-access"></a>Initialisation et accès des membres

L’exemple suivant montre comment déclarer un pointeur brut et l’initialiser avec un objet alloué sur le tas, puis comment l’utiliser. Il montre également quelques-uns des dangers associés aux pointeurs bruts. (Rappelez-vous, c’est la programmation de style C et non pas moderne C'!)

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

## <a name="pointer-arithmetic-and-arrays"></a>Arithmétique et tableaux de pointeur

Les pointeurs et les tableaux sont étroitement liés. Lorsqu’un tableau est transmis par valeur à une fonction, il est passé comme pointeur du premier élément. L’exemple suivant montre les propriétés importantes suivantes des pointeurs et des tableaux :

- l’opérateur `sizeof` retourne la taille totale dans les octets d’un tableau
- pour déterminer le nombre d’éléments, diviser les octets totaux par la taille d’un élément
- lorsqu’un tableau est transmis à une fonction, il *se désintègre* à un type de pointeur
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

Certaines opérations arithmétiques peuvent être effectuées sur des pointeurs non-const pour les faire pointer vers un nouvel emplacement de mémoire. Un pointeur peut être incrémenté et **++** **+=** décroissé à l’aide de la , , **-=** et **--** les opérateurs. Cette technique peut être utilisée dans les tableaux et est particulièrement utile dans les tampons de données non saisies. Un **\* vide** incréments de la taille d’un **omble** (1 byte). Un pointeur dactylographié incréments par taille du type qu’il pointe vers.

L’exemple suivant montre comment l’arithmétique pointeur peut être utilisée pour accéder à des pixels individuels dans un bitmap sur Windows. Notez l’utilisation de **nouveau** et **supprimer**, et l’opérateur de déreférence.

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

## <a name="void-pointers"></a>pointeurs voidMD

Un pointeur à **vider** indique simplement un emplacement de mémoire brut. Parfois, il est nécessaire d’utiliser des pointeurs **vides,\* ** par exemple lors de la transmission entre le code C et les fonctions C.

Lorsqu’un pointeur dactylographié est projeté sur un pointeur vide, le contenu de l’emplacement de la mémoire n’est pas modifié, mais les informations de type sont perdues, de sorte que vous ne pouvez pas effectuer des opérations d’augmentation ou de décroissement. Un emplacement de mémoire peut être jeté, par exemple, de MyClassMD à vide et revenir à MyClass. Ces opérations sont intrinsèquement sujettes aux erreurs et nécessitent un grand soin pour éviter les erreurs. Le Cmd moderne décourage l’utilisation de pointeurs vides à moins que cela ne soit absolument nécessaire.

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
    char* pchar = static_cast<char*>(pvoid);
    for(char* c = pchar; c < pchar + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Pointeurs aux fonctions

Dans la programmation de style C, les pointeurs de fonction sont utilisés principalement pour transmettre des fonctions à d’autres fonctions. Dans ce scénario, l’appelant peut personnaliser le comportement d’une fonction sans la modifier. Dans le C moderne, les [expressions lambda](lambda-expressions-in-cpp.md) offrent la même capacité avec une plus grande sécurité de type et d’autres avantages.

Une déclaration de pointeur de fonction précise la signature que la fonction pointue doit avoir :

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

L’exemple suivant `combine` montre une fonction qui prend comme `std::string` paramètre `std::string`toute fonction qui accepte un et renvoie un . Selon la fonction qui `combine` lui est transmise, elle prépendra ou ajoutera une ficelle.

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

[Smart pointeurs](smart-pointers-modern-cpp.md)
[Indirection Operator:](indirection-operator-star.md)<br/>
[address-of, opérateur](address-of-operator-amp.md)</br>
[Bienvenue à C](welcome-back-to-cpp-modern-cpp.md)
