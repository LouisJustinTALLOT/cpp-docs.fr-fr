---
description: 'En savoir plus sur : types de paramètres d’attribut (C++/CLI et C++/CX)'
title: Types de paramètre d’attribut (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
ms.openlocfilehash: 7f2d5dd2def4e61d5b2b0406cc193bf818bc3d9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97177092"
---
# <a name="attribute-parameter-types--ccli-and-ccx"></a>Types de paramètre d’attribut (C++/CLI et C++/CX)

Les valeurs passées aux attributs doivent être connues du compilateur au moment de la compilation.  Les paramètres d’attribut peuvent appartenir aux types suivants :

- **`bool`**

- **`char`**, **`unsigned char`**

- **`short`**, **`unsigned short`**

- **`int`**, **`unsigned int`**

- **`long`**, **`unsigned long`**

- **`__int64`**, **non signé __int64**

- **`float`**, **`double`**

- **`wchar_t`**

- **`char*`** ou `wchar_t*` ou `System::String*`

- `System::Type ^`

- `System::Object ^`

- **`enum`**

## <a name="example-attribute-parameter-types"></a>Exemple : types de paramètres d’attribut

### <a name="code"></a>Code

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example-unnamed-arguments-precede-named-arguments"></a>Exemple : les arguments sans nom précèdent les arguments nommés

### <a name="description"></a>Description

Lorsque vous spécifiez des attributs, tous les arguments (positionnels) non nommés doivent précéder les arguments nommés.

### <a name="code"></a>Code

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example-one-dimensional-array-attribute-parameter"></a>Exemple : paramètre d’attribut de tableau unidimensionnel

### <a name="description"></a>Description

Les paramètres d’attribut peuvent être des tableaux unidimensionnels des types précédents.

### <a name="code"></a>Code

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>Voir aussi

[Attributs définis par l’utilisateur](user-defined-attributes-cpp-component-extensions.md)
