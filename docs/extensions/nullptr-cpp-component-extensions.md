---
title: nullptr (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- __nullptr keyword (C++)
- nullptr keyword [C++]
ms.assetid: 594cfbf7-06cb-4366-9ede-c0b703e1d095
ms.openlocfilehash: 05aaaa8a0d0056e0f5318f5e9329d90824760728
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515634"
---
# <a name="nullptr--ccli-and-ccx"></a>nullptr (C++/CLI et C++/CX)

Le mot clé **nullptr** représente une *valeur de pointeur null*. Utilisez une valeur de pointeur null pour indiquer qu’un descripteur d’objet, un pointeur intérieur ou un type de pointeur natif ne pointent pas vers un objet.

Utilisez **nullptr** avec du code managé ou natif. Le compilateur émet des instructions appropriées mais différentes pour les valeurs de pointeur null natives et managées. Pour plus d’informations sur l’utilisation de la version ISO C++ standard de ce mot clé, consultez [nullptr](../cpp/nullptr.md).

Le mot clé **__nullptr** spécifique à Microsoft a la même signification que **nullptr**, mais il s’applique uniquement au code natif. Si vous utilisez **nullptr** avec du code C/C++ natif et que vous le compilez avec l’option du compilateur [/clr](../build/reference/clr-common-language-runtime-compilation.md), le compilateur ne peut pas déterminer si **nullptr** indique une valeur de pointeur null managée ou native. Pour que vos intentions soient claires pour le compilateur, utilisez le mot clé **nullptr** pour spécifier une valeur managée et **__nullptr** pour spécifier une valeur native.

Le mot clé **nullptr** est équivalent à **Nothing** dans Visual Basic et à **null** dans C#.

## <a name="usage"></a>Utilisation

Le mot clé **nullptr** peut être utilisé partout où un descripteur, un pointeur natif ou un argument de fonction peut être utilisé.

Le mot clé **nullptr** n’est pas un type et n’est pas pris en charge pour une utilisation avec :

- [sizeof](../cpp/sizeof-operator.md)

- [typeid](../cpp/typeid-operator.md)

- `throw nullptr` (bien que `throw (Object^)nullptr;` fonctionne)

Le mot clé **nullptr** peut être utilisé lors de l’initialisation des types de pointeur suivants :

- Pointeur natif

- Descripteur Windows Runtime

- Descripteur managé

- Pointeur intérieur managé

Le mot clé **nullptr** peut être utilisé pour tester si une référence de pointeur ou de descripteur est null avant qu’elle ne soit utilisée.

Les appels de fonction dans les langages qui utilisent des valeurs de pointeur null pour la vérification des erreurs doivent être interprétés correctement.

Vous ne pouvez pas initialiser un descripteur à zéro ; seul le mot clé **nullptr** peut être utilisé. L’affectation de la constante 0 pour un descripteur d’objet produit un `Int32` boxed et effectue un cast dans `Object^`.

## <a name="example"></a>Exemple

L’exemple de code suivant montre que le mot clé **nullptr** peut être utilisé partout où un descripteur, un pointeur natif, ou un argument de fonction peuvent être utilisés. Et l’exemple montre que le mot clé **nullptr** peut être utilisé pour vérifier une référence avant de l’utiliser.

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

L’exemple de code suivant montre que le mot clé **nullptr** et zéro peuvent être utilisés indifféremment sur les pointeurs natifs.

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

L’exemple de code suivant montre que **nullptr** est interprété comme un descripteur ou un pointeur natif pour tous les types. En cas de surcharge de fonction avec des descripteurs vers des types différents, une erreur d’ambiguïté sera générée. Le mot clé **nullptr** doit être converti de manière explicite vers le type.

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

L’exemple de code suivant montre la conversion de **nullptr** est autorisée et retourne un pointeur ou un descripteur vers le type de cast qui contient la valeur **nullptr**.

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

L’exemple de code suivant montre que lorsque les descripteurs ne sont pas déclarés et initialisés explicitement, ils sont initialisés par défaut pour **nullptr**.

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

L’exemple de code suivant montre que le mot clé **nullptr** peut être affecté à un pointeur natif quand vous le compilez avec `/clr`.

```cpp
// mcpp_nullptr_6.cpp
// compile with: /clr
int main() {
   int * i = 0;
   int * j = nullptr;
}
```

## <a name="requirements"></a>Spécifications

Option du compilateur : (Non requis ; pris en charge par toutes les options de génération de code, y compris `/ZW` et `/clr`)

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)<br/>
[nullptr](../cpp/nullptr.md)