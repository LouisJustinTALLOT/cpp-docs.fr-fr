---
title: nullptr (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 5e7a5d3f9a42968dee35f82d3f19d0fdb6da5d0c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214228"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI et C++/CX)

Le **`nullptr`** mot clé représente une *valeur de pointeur null*. Utilisez une valeur de pointeur null pour indiquer qu’un descripteur d’objet, un pointeur intérieur ou un type de pointeur natif ne pointent pas vers un objet.

Utilisez **`nullptr`** avec le code managé ou natif. Le compilateur émet des instructions appropriées mais différentes pour les valeurs de pointeur null natives et managées. Pour plus d’informations sur l’utilisation de la version ISO C++ standard de ce mot clé, consultez [nullptr](../cpp/nullptr.md).

Le mot clé **__nullptr** est un mot clé spécifique à Microsoft qui a la même signification que **`nullptr`** , mais s’applique uniquement au code natif. Si vous utilisez **`nullptr`** avec du code C/C++ natif, puis compilez avec l’option de compilateur [/CLR](../build/reference/clr-common-language-runtime-compilation.md) , le compilateur ne peut pas déterminer si **`nullptr`** indique une valeur de pointeur null native ou managée. Pour que votre intention soit claire pour le compilateur, utilisez **`nullptr`** pour spécifier une valeur managée ou **__nullptr** pour spécifier une valeur native.

Le **`nullptr`** mot clé est équivalent à **Nothing** dans Visual Basic et **null** en C#.

## <a name="usage"></a>Usage

Le **`nullptr`** mot clé peut être utilisé partout où il est possible d’utiliser un handle, un pointeur natif ou un argument de fonction.

Le **`nullptr`** mot clé n’est pas un type et n’est pas pris en charge pour une utilisation avec :

- [sizeof](../cpp/sizeof-operator.md)

- [TypeId](../cpp/typeid-operator.md)

- `throw nullptr` (bien que `throw (Object^)nullptr;` fonctionne)

Le **`nullptr`** mot clé peut être utilisé dans l’initialisation des types de pointeurs suivants :

- Pointeur natif

- Descripteur Windows Runtime

- Descripteur managé

- Pointeur intérieur managé

Le **`nullptr`** mot clé peut être utilisé pour tester si un pointeur ou une référence de handle a la valeur null avant que la référence soit utilisée.

Les appels de fonction dans les langages qui utilisent des valeurs de pointeur null pour la vérification des erreurs doivent être interprétés correctement.

Vous ne pouvez pas initialiser un handle à zéro ; seul **`nullptr`** peut être utilisé. L’affectation de la constante 0 pour un descripteur d’objet produit un `Int32` boxed et effectue un cast dans `Object^`.

## <a name="example"></a>Exemple

L’exemple de code suivant montre que le **`nullptr`** mot clé peut être utilisé partout où un handle, un pointeur natif ou un argument de fonction peut être utilisé. Et l’exemple montre que le **`nullptr`** mot clé peut être utilisé pour vérifier une référence avant son utilisation.

```cpp
// mcpp_nullptr.cpp
// compile with: /clr
value class V {};
ref class G {};
void f(System::Object ^) {}

int main() {
// Native pointer.
   int *pN = nullptr;
// Managed handle.
   G ^pG = nullptr;
   V ^pV1 = nullptr;
// Managed interior pointer.
   interior_ptr<V> pV2 = nullptr;
// Reference checking before using a pointer.
   if (pN == nullptr) {}
   if (pG == nullptr) {}
   if (pV1 == nullptr) {}
   if (pV2 == nullptr) {}
// nullptr can be used as a function argument.
   f(nullptr);   // calls f(System::Object ^)
}
```

## <a name="example"></a>Exemple

L’exemple de code suivant montre que **`nullptr`** et zéro peut être utilisé de manière interchangeable sur des pointeurs natifs.

```cpp
// mcpp_nullptr_1.cpp
// compile with: /clr
class MyClass {
public:
   int i;
};

int main() {
   MyClass * pMyClass = nullptr;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");

   pMyClass = 0;
   if ( pMyClass == nullptr)
      System::Console::WriteLine("pMyClass == nullptr");

   if ( pMyClass == 0)
      System::Console::WriteLine("pMyClass == 0");
}
```

```Output
pMyClass == nullptr

pMyClass == 0

pMyClass == nullptr

pMyClass == 0
```

## <a name="example"></a>Exemple

L’exemple de code suivant montre que **`nullptr`** est interprété comme un handle de tout type ou un pointeur natif vers n’importe quel type. En cas de surcharge de fonction avec des descripteurs vers des types différents, une erreur d’ambiguïté sera générée. Doit **`nullptr`** être explicitement casté en type.

```cpp
// mcpp_nullptr_2.cpp
// compile with: /clr /LD
void f(int *){}
void f(int ^){}

void f_null() {
   f(nullptr);   // C2668
   // try one of the following lines instead
   f((int *) nullptr);
   f((int ^) nullptr);
}
```

## <a name="example"></a>Exemple

L’exemple de code suivant montre que la conversion **`nullptr`** est autorisée et retourne un pointeur ou un handle vers le type de cast qui contient la **`nullptr`** valeur.

```cpp
// mcpp_nullptr_3.cpp
// compile with: /clr /LD
using namespace System;
template <typename T>
void f(T) {}   // C2036 cannot deduce template type because nullptr can be any type

int main() {
   f((Object ^) nullptr);   // T = Object^, call f(Object ^)

   // Delete the following line to resolve.
   f(nullptr);

   f(0);   // T = int, call f(int)
}
```

## <a name="example"></a>Exemple

L’exemple de code suivant montre que **`nullptr`** peut être utilisé comme paramètre de fonction.

```cpp
// mcpp_nullptr_4.cpp
// compile with: /clr
using namespace System;
void f(Object ^ x) {
   Console::WriteLine("test");
}

int main() {
   f(nullptr);
}
```

```Output
test
```

## <a name="example"></a>Exemple

L’exemple de code suivant montre que lorsque les handles sont déclarés et ne sont pas explicitement initialisés, ils sont initialisés par défaut à **`nullptr`** .

```cpp
// mcpp_nullptr_5.cpp
// compile with: /clr
using namespace System;
ref class MyClass {
public:
   void Test() {
      MyClass ^pMyClass;   // gc type
      if (pMyClass == nullptr)
         Console::WriteLine("NULL");
   }
};

int main() {
   MyClass ^ x = gcnew MyClass();
   x -> Test();
}
```

```Output
NULL
```

## <a name="example"></a>Exemple

L’exemple de code suivant montre qu' **`nullptr`** il est possible d’assigner à un pointeur natif quand vous compilez avec `/clr` .

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Spécifications

Option du compilateur : (non obligatoire ; prise en charge par toutes les options de génération de code, y compris `/ZW` et `/clr` )

## <a name="see-also"></a>Voir aussi

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)
