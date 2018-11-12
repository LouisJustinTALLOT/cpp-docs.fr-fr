---
title: nullptr (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 5d2a2a679beca3929622c93d71412661713859f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474007"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++ / c++ / CLI et c++ / CX)

Le **nullptr** mot clé représente un *valeur de pointeur null*. Utilisez une valeur de pointeur null pour indiquer qu’un handle d’objet, un pointeur intérieur ou un type de pointeur natif ne pointe pas vers un objet.

Utilisez **nullptr** avec du code managé ou natif. Le compilateur émet des instructions appropriées, mais différents pour les valeurs de pointeur null natif et managé. Pour plus d’informations sur l’utilisation de la version de C++ ISO standard de ce mot clé, consultez [nullptr](../cpp/nullptr.md).

Le **__nullptr** mot clé est un mot clé spécifique de Microsoft qui a la même signification que **nullptr**, mais s’applique uniquement en code natif. Si vous utilisez **nullptr** avec C/C++ natif de code, puis compilez avec le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur, le compilateur ne peut pas déterminer si **nullptr** indique native ou géré la valeur de pointeur null. Pour rendre votre intention claires pour le compilateur, utilisez **nullptr** pour spécifier une valeur managée ou **__nullptr** pour spécifier une valeur native.

Le **nullptr** mot clé est équivalente à **rien** en Visual Basic et **null** en c#.

## <a name="usage"></a>Utilisation

Le **nullptr** mot clé peut être utilisé partout où un handle, un pointeur natif ou un argument de fonction peut être utilisée.

Le **nullptr** mot clé n’est pas un type et n’est pas pris en charge pour une utilisation avec :

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (bien que `throw (Object^)nullptr;` fonctionnera)

Le **nullptr** mot clé peut être utilisé lors de l’initialisation des types pointeur suivants :

- Pointeur natif

- Handle Windows Runtime

- Handle géré

- Pointeur intérieur managé

Le **nullptr** mot clé peut être utilisé pour tester si une référence de pointeur ou handle est null avant que la référence est utilisée.

Parmi les langages qui utilisent des valeurs de pointeur null pour la vérification des erreurs, les appels de fonction doivent être interprétés correctement.

Vous ne pouvez pas initialiser un handle à zéro ; uniquement **nullptr** peut être utilisé. Affectation de la constante 0 pour un handle d’objet produit boxed `Int32` et un cast en `Object^`.

## <a name="example"></a>Exemple

L’exemple de code suivant montre que le **nullptr** mot clé peut être utilisée partout où un handle, un pointeur natif, ou l’argument de fonction peut être utilisé. Et l’exemple montre que le **nullptr** mot clé peut être utilisée pour vérifier une référence avant de les utiliser.

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

L’exemple de code suivant montre que **nullptr** et zéro peut être utilisé indifféremment sur les pointeurs natifs.

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

L’exemple de code suivant montre que **nullptr** est interprété comme un handle vers n’importe quel type ou un pointeur natif à n’importe quel type. En cas de surcharge de fonction avec des handles vers des types différents, une erreur d’ambiguïté sera générée. Le **nullptr** devra être explicitement converti en un type.

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

L’exemple de code suivant montre ce cast **nullptr** est autorisé et retourne un pointeur ou un handle vers le type de cast qui contient le **nullptr** valeur.

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

L’exemple de code suivant montre que **nullptr** peut être utilisé comme paramètre de fonction.

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

L’exemple de code suivant montre que lorsque les handles sont déclarés et initialisés pas explicitement, ils sont initialisés à par défaut **nullptr**.

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

L’exemple de code suivant montre que **nullptr** peuvent être affectés à un pointeur natif quand vous compilez avec `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Configuration requise

Option du compilateur : (non requis ; pris en charge par toutes les options de génération de code, y compris `/ZW` et `/clr`)

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](../windows/component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)