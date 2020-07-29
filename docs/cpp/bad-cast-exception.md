---
title: bad_cast, exception
ms.date: 10/04/2019
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 2efe5be5e44751831a56b29cfc629df2d21843f7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229179"
---
# <a name="bad_cast-exception"></a>bad_cast, exception

L’exception **bad_cast** est levée par l' **`dynamic_cast`** opérateur en raison de l’échec d’un cast en un type référence.

## <a name="syntax"></a>Syntaxe

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Notes

L’interface pour **bad_cast** est :

```cpp
class bad_cast : public exception
```

Le code suivant contient un exemple d’échec de **`dynamic_cast`** la levée de l’exception **bad_cast** .

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo>
#include <iostream>

class Shape {
public:
   virtual void virtualfunc() const {}
};

class Circle: public Shape {
public:
   virtual void virtualfunc() const {}
};

using namespace std;
int main() {
   Shape shape_instance;
   Shape& ref_shape = shape_instance;
   try {
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);
   }
   catch (bad_cast b) {
      cout << "Caught: " << b.what();
   }
}
```

L’exception est levée, car l’objet en cours de conversion (une forme) n’est pas dérivé du type de cast spécifié (Circle). Pour éviter l'exception, ajoutez les déclarations ci-dessous à `main` :

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

Puis inversez le sens du cast dans le **`try`** bloc comme suit :

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="members"></a>Membres

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[bad_cast](#bad_cast)|Constructeur des objets de type `bad_cast`.|

### <a name="functions"></a>Fonctions

|Fonction|Description|
|-|-|
|[données](#what)|TBD|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur =](#op_eq)|Opérateur d’assignation qui assigne un `bad_cast` objet à un autre.|

## <a name="bad_cast"></a><a name="bad_cast"></a>bad_cast

Constructeur des objets de type `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="operator"></a><a name="op_eq"></a>opérateur =

Opérateur d’assignation qui assigne un `bad_cast` objet à un autre.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a><a name="what"></a>données

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Voir aussi

[Opérateur dynamic_cast](../cpp/dynamic-cast-operator.md)\
[Mot](../cpp/keywords-cpp.md)\
[Meilleures pratiques C++ modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)
