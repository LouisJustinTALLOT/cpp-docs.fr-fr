---
title: typeid (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- typeid keyword [C++]
ms.assetid: e9706cae-e7c4-4d6d-b474-646d73df3e70
ms.openlocfilehash: ec64388d5f71cff01207129e337cf20bb151db1a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515984"
---
# <a name="typeid--ccli-and-ccx"></a>typeid (C++/CLI et C++/CX)

Obtient une valeur qui indique le type d’un objet.

> [!NOTE]
> Cette rubrique fait référence à la version des extensions de composant de typeid. Pour la version ISO C++ de ce mot clé, consultez [Opérateur typeid](../cpp/typeid-operator.md).

## <a name="all-runtimes"></a>Tous les runtimes

### <a name="syntax"></a>Syntaxe

```cpp
T::typeid
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un nom de type.

## <a name="windows-runtime"></a>Windows Runtime

### <a name="syntax"></a>Syntaxe

```cpp
Platform::Type^ type = T::typeid;
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Un nom de type.

### <a name="remarks"></a>Remarques

Dans C++/CX, typeid retourne une classe [Platform::Type](../cppcx/platform-type-class.md) qui est construite à partir des informations sur le type de runtime.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="syntax"></a>Syntaxe

```
type::typeid
```

### <a name="parameters"></a>Paramètres

*type*<br/>
Le nom d’un type (déclarateur abstrait) dont vous souhaitez l’objet `System::Type`.

### <a name="remarks"></a>Remarques

`typeid` est utilisé pour obtenir le <xref:System.Type> d’un type au moment de la compilation.

`typeid` est similaire à l’obtention de la classe System::Type pour un type au moment de l’exécution à l’aide de <xref:System.Type.GetType%2A> ou <xref:System.Object.GetType%2A>. Toutefois, typeid accepte uniquement un nom de type en tant que paramètre.  Si vous souhaitez utiliser une instance d’un type pour obtenir son nom System::Type, utilisez GetType.

`typeid` doit pouvoir évaluer un nom de type (type) au moment de la compilation, tandis que GetType évalue le type à retourner au moment de l’exécution.

`typeid` peut prendre un nom de type natif ou un alias de runtime langage commun pour le nom de type natif. Consultez [Équivalents .NET Framework des types natifs C++ (C++-CLI)](../dotnet/dotnet-framework-equivalents-to-cpp-native-types-cpp-cli.md) pour plus d’informations.

`typeid` fonctionne également avec les types natifs, bien qu’il retourne toujours une classe System::Type.  Pour obtenir une structure type_info, utilisez l’[opérateur typeid](../cpp/typeid-operator.md).

### <a name="requirements"></a>Spécifications

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant compare le mot clé typeid au membre `GetType()`.

```cpp
// keyword__typeid.cpp
// compile with: /clr
using namespace System;

ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   Type ^ pType = pG->GetType();
   Type ^ pType2 = G::typeid;

   if (pType == pType2)
      Console::WriteLine("typeid and GetType returned the same System::Type");
   Console::WriteLine(G::typeid);

   typedef float* FloatPtr;
   Console::WriteLine(FloatPtr::typeid);
}
```

```Output
typeid and GetType returned the same System::Type
G

System.Single*
```

L’exemple suivant montre qu’une variable de type System::type peut être utilisée pour obtenir les attributs sur un type.  Il montre également que pour certains types, vous devez créer un typedef pour utiliser `typeid`.

```cpp
// keyword__typeid_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Security;
using namespace System::Security::Permissions;

typedef int ^ handle_to_int;
typedef int * pointer_to_int;

public ref class MyClass {};

class MyClass2 {};

[attribute(AttributeTargets::All)]
ref class AtClass {
public:
   AtClass(Type ^) {
      Console::WriteLine("in AtClass Type ^ constructor");
   }
};

[attribute(AttributeTargets::All)]
ref class AtClass2 {
public:
   AtClass2() {
      Console::WriteLine("in AtClass2 constructor");
   }
};

// Apply the AtClass and AtClass2 attributes to class B
[AtClass(MyClass::typeid), AtClass2]
[AttributeUsage(AttributeTargets::All)]
ref class B : Attribute {};

int main() {
   Type ^ MyType = B::typeid;

   Console::WriteLine(MyType->IsClass);

   array<Object^>^ MyArray = MyType -> GetCustomAttributes(true);
   for (int i = 0 ; i < MyArray->Length ; i++ )
      Console::WriteLine(MyArray[i]);

   if (int::typeid != pointer_to_int::typeid)
      Console::WriteLine("int::typeid != pointer_to_int::typeid, as expected");

   if (int::typeid == handle_to_int::typeid)
      Console::WriteLine("int::typeid == handle_to_int::typeid, as expected");
}
```

```Output
True

in AtClass2 constructor

in AtClass Type ^ constructor

AtClass2

System.AttributeUsageAttribute

AtClass

int::typeid != pointer_to_int::typeid, as expected

int::typeid == handle_to_int::typeid, as expected
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)