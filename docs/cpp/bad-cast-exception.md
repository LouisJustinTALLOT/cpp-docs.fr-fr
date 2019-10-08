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
ms.openlocfilehash: 7384394fb53c6aa4bc009a903ba0ed22bf0ed0d6
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998772"
---
# <a name="bad_cast-exception"></a>bad_cast, exception

L’exception **bad_cast** est levée par l’opérateur **dynamic_cast** suite à un échec de conversion en type référence.

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

Le code suivant contient un exemple d’échec de **dynamic_cast** qui lève l’exception **bad_cast** .

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

Ensuite, inversez le sens du cast dans le bloc **try** comme suit :

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
|[what](#what)|TBD|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator=](#op_eq)|Opérateur d’assignation qui assigne un objet `bad_cast` à un autre.|

## <a name="bad_cast"></a>bad_cast

Constructeur des objets de type `bad_cast`.

```cpp
bad_cast(const char * _Message = "bad cast");
bad_cast(const bad_cast &);
```

## <a name="op_eq"></a>opérateur =

Opérateur d’assignation qui assigne un objet `bad_cast` à un autre.

```cpp
bad_cast& operator=(const bad_cast&) noexcept;
```

## <a name="what"></a>données

```cpp
const char* what() const noexcept override;
```

## <a name="see-also"></a>Voir aussi

@no__t d' [opérateur dynamic_cast](../cpp/dynamic-cast-operator.md)-1
[Mots clés](../cpp/keywords-cpp.md)\
[Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)
