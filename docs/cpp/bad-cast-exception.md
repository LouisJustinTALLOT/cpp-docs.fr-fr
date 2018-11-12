---
title: bad_cast, exception
ms.date: 11/04/2016
f1_keywords:
- bad_cast
- bad_cast_cpp
helpviewer_keywords:
- exceptions [C++], bad_cast
- bad_cast keyword [C++]
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
ms.openlocfilehash: 028fa8cc90b33aca6a37fb3b7f58b8c5fad81bd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573343"
---
# <a name="badcast-exception"></a>bad_cast, exception

Le **bad_cast** exception est levée par le **dynamic_cast** opérateur à la suite d’un échec de cast à un type référence.

## <a name="syntax"></a>Syntaxe

```
catch (bad_cast)
   statement
```

## <a name="remarks"></a>Notes

L’interface pour **bad_cast** est :

```cpp
class bad_cast : public exception {
public:
   bad_cast(const char * _Message = "bad cast");
   bad_cast(const bad_cast &);
   virtual ~bad_cast();
};
```

Le code suivant contient un exemple d’un échec **dynamic_cast** qui lève la **bad_cast** exception.

```cpp
// expre_bad_cast_Exception.cpp
// compile with: /EHsc /GR
#include <typeinfo.h>
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

L'exception est levée car l'objet du cast (Shape) n'est pas dérivé du type de cast spécifié (Circle). Pour éviter l'exception, ajoutez les déclarations ci-dessous à `main` :

```cpp
Circle circle_instance;
Circle& ref_circle = circle_instance;
```

Puis changez le sens du cast dans le **essayez** bloquer comme suit :

```cpp
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);
```

## <a name="see-also"></a>Voir aussi

[dynamic_cast, opérateur](../cpp/dynamic-cast-operator.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)