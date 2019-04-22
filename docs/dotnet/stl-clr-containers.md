---
title: STL/CLR, conteneurs
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR, containers
- containers, STL/CLR
ms.assetid: 34ca8031-2041-46b9-aed9-29082d1972ea
ms.openlocfilehash: dc2e5ce3263c61839a1ba434ab0d2a39e6a9078f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58774540"
---
# <a name="stlclr-containers"></a>STL/CLR, conteneurs

La bibliothèque STL/CLR se compose de conteneurs qui sont similaires à ceux trouvés dans la bibliothèque Standard C++, mais elle s’exécute dans un environnement managé du .NET Framework. Il n’est pas mis à jour avec la bibliothèque Standard C++ réelle et est conservé pour la prise en charge héritée.

Ce document fournit une vue d'ensemble des conteneurs dans STL/CLR, tels que les conditions requises pour les éléments conteneurs, les types d'éléments que vous pouvez insérer dans des conteneurs, et les problèmes de propriété avec les éléments des conteneurs. Le cas échéant, les différences entre la bibliothèque Standard C++ native et STL/CLR sont indiquées.

## <a name="requirements-for-container-elements"></a>Exigences pour les éléments de conteneurs

Tous les éléments insérés dans les conteneurs STL/CLR doivent obéir à certaines instructions. Pour plus d’informations, consultez [exigences pour les éléments de conteneur STL/CLR](../dotnet/requirements-for-stl-clr-container-elements.md).

## <a name="valid-container-elements"></a>Éléments de conteneurs valides

Les conteneurs STL/CLR peuvent contenir l'un des deux types d'éléments :

- Handle vers des types référence.

- Types référence.

- Types de valeurs non encapsulés.

Vous ne pouvez pas insérer les valeurs de type encapsulé dans les conteneurs STL/CLR.

### <a name="handles-to-reference-types"></a>Handle vers des types référence

Vous pouvez insérer un handle à un type référence dans un conteneur STL/CLR. Un descripteur en C++ qui cible le CLR est analogue à un pointeur en mode natif C++. Pour plus d’informations, consultez [gérer sur l’opérateur Object (^)](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md).

#### <a name="example"></a>Exemple

L’exemple suivant montre comment insérer un handle vers un objet Employee dans un [cliext::set](../dotnet/set-stl-clr.md).

```
// cliext_container_valid_reference_handle.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee^ empl1419 = gcnew Employee();
    empl1419->Name = L"Darin Lockert";
    empl1419->EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee^>^ emplSet = gcnew set<Employee^>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="reference-types"></a>Types référence

Il est également possible d'insérer un type référence (plutôt qu'un handle à un type de référence) dans un conteneur STL/CLR. La principale différence ici est que lorsqu'un conteneur de types référence est supprimé, le destructeur est appelé pour tous les éléments du conteneur. Dans un conteneur de handles vers des types référence, les destructeurs de ces éléments ne seraient pas appelés.

#### <a name="example"></a>Exemple

L'exemple suivant indique comment insérer un objet Employee dans un `cliext::set`.

```
// cliext_container_valid_reference.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

ref class Employee
{
public:
    // STL/CLR containers might require a public constructor, so it
    // is a good idea to define one.
    Employee() :
        name(nullptr),
        employeeNumber(0) { }

    // All STL/CLR containers require a public copy constructor.
    Employee(const Employee% orig) :
        name(orig.name),
        employeeNumber(orig.employeeNumber) { }

    // All STL/CLR containers require a public assignment operator.
    Employee% operator=(const Employee% orig)
    {
        if (this != %orig)
        {
            name = orig.name;
            employeeNumber = orig.employeeNumber;
        }

        return *this;
    }

    // All STL/CLR containers require a public destructor.
    ~Employee() { }

    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee^ empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl->EmployeeNumber, empl->Name);
    }

    return 0;
}
```

### <a name="unboxed-value-types"></a>Types de valeurs non encapsulés

Vous pouvez également insérer un type de valeur non encapsulé dans un conteneur STL/CLR. Un type valeur unboxed est un type valeur qui n’a pas été *boxed* dans un type référence.

Un élément de type valeur peut être l'un des types de valeurs standard, comme `int`, ou il peut s'agir d'un type défini par l'utilisateur, tel que `value class`. Pour plus d’informations, consultez [Classes et Structs](../extensions/classes-and-structs-cpp-component-extensions.md)

#### <a name="example"></a>Exemple

L'exemple suivant modifie le premier exemple en transformant la classe Employee en un type de valeur. Ce type de valeur est alors inséré dans `cliext::set` comme dans le premier exemple.

```
// cliext_container_valid_valuetype.cpp
// compile with: /clr

#include <cliext/set>

using namespace cliext;
using namespace System;

value class Employee
{
public:
    // Associative containers such as maps and sets
    // require a comparison operator to be defined
    // to determine proper ordering.
    bool operator<(const Employee^ rhs)
    {
        return (employeeNumber < rhs->employeeNumber);
    }

    // The employee's name.
    property String^ Name
    {
        String^ get() { return name; }
        void set(String^ value) { name = value; }
    }

    // The employee's employee number.
    property int EmployeeNumber
    {
        int get() { return employeeNumber; }
        void set(int value) { employeeNumber = value; }
    }

private:
    String^ name;
    int employeeNumber;
};

int main()
{
    // Create a new employee object.
    Employee empl1419;
    empl1419.Name = L"Darin Lockert";
    empl1419.EmployeeNumber = 1419;

    // Add the employee to the set of all employees.
    set<Employee>^ emplSet = gcnew set<Employee>();
    emplSet->insert(empl1419);

    // List all employees of the company.
    for each (Employee empl in emplSet)
    {
        Console::WriteLine("Employee Number {0}: {1}",
            empl.EmployeeNumber, empl.Name);
    }

    return 0;
}
```

Si vous tentez d’insérer un handle vers un type valeur dans un conteneur, [erreur du compilateur C3225](../error-messages/compiler-errors-2/compiler-error-c3225.md) est généré.

### <a name="performance-and-memory-implications"></a>Conséquences de performances et de mémoire

Vous devez considérer plusieurs facteurs pour déterminer s'il faut utiliser des handles vers des types référence ou des types de valeurs en tant qu'éléments de conteneur. Si vous décidez d'utiliser des types de valeur, n'oubliez pas qu'une copie de l'élément est effectuée chaque fois qu'un élément est inséré dans le conteneur. Pour les petits objets, ce ne doit pas être un problème , mais si les objets à insérer sont volumineux, les performances peuvent en pâtir. De plus, si vous utilisez des types de valeurs, il est impossible d'inscrire un élément dans plusieurs conteneurs en même temps puisque chaque conteneur aurait sa propre copie de l'élément.

Si vous décidez d'utiliser des handles vers des types référence à la place, les performances peuvent s'améliorer car il n'est pas nécessaire d'effectuer une copie de l'élément lorsqu'il est inséré dans le conteneur. En outre, contrairement à des types de valeur, le même élément peut exister dans plusieurs conteneurs. Toutefois, si vous décidez d'utiliser les handles, vous devez veiller à vérifier que le handle est valide et que l'objet auquel il se rapporte n'a pas été supprimé ailleurs dans le programme.

## <a name="ownership-issues-with-containers"></a>Problèmes de propriété avec les conteneurs

Les conteneurs en STL/CLR travaillent sur la sémantique de la valeur. Chaque fois que vous insérez un élément dans un conteneur, une copie de cet élément est insérée. Si vous souhaitez obtenir la sémantique comme référence, vous pouvez insérer un descripteur sur un objet au lieu de l'objet lui-même.

Lorsque vous appelez une méthode clear ou erase d'un conteneur de handles d'objets, les objets qui sont référencés ne sont pas libérés de la mémoire. Vous devez soit supprimer l’objet explicitement, ou, puisque ces objets résident sur le tas managé, activer le garbage collector pour libérer de la mémoire une fois qu’il a déterminé si l’objet n’est plus utilisé.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
