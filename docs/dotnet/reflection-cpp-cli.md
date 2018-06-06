---
title: Réflexion (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d41d7f627a50dd1a09f4256fbd8448d82c6d5f27
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705242"
---
# <a name="reflection-ccli"></a>Réflexion (C++/CLI)

La réflexion permet des types de données connus être inspectée au moment de l’exécution. La réflexion permet l’énumération des types de données dans un assembly donné, et les membres d’un type de classe ou de valeur donné peuvent être détectés. Cela est vrai quel que soit le si le type a été appelé ou référencé au moment de la compilation. C’est donc une fonctionnalité utile pour le développement et les outils de gestion de code.

Notez que le nom d’assembly fourni est le nom fort (consultez [création et assemblys avec nom fort](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), qui inclut la version de l’assembly, la culture et les informations de signature. Notez également que le nom de l’espace de noms dans lequel le type de données est défini peut être récupéré, ainsi que le nom de la classe de base.

La méthode la plus courante pour accéder aux fonctionnalités de réflexion s’effectue via le <xref:System.Object.GetType%2A> (méthode). Cette méthode est fournie par [System::Object](https://msdn.microsoft.com/en-us/library/system.object.aspx), à partir de laquelle dérivent toutes les classes par le garbage collector.

> [!NOTE]
> La réflexion sur un .exe générées avec le compilateur Visual C++ est autorisée uniquement si le .exe est généré avec la **/CLR : pure** ou **/CLR : safe** options du compilateur. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non disponibles dans Visual Studio 2017. Consultez [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) pour plus d’informations.

Pour plus d’informations, consultez [System.Reflection Namespace](https://msdn.microsoft.com/en-us/library/system.reflection.aspx)

## <a name="example-gettype"></a>Exemple : GetType

Le `GetType` méthode retourne un pointeur vers un <xref:System.Type> objet de classe, qui décrit le type sur lorsque l’objet est basé. (Le **Type** objet ne contient pas toutes les informations spécifiques à l’instance.) Un de ces éléments est le nom complet du type, qui peut être affiché comme suit :

Notez que le nom du type inclut toute la portée dans laquelle le type est défini, y compris l’espace de noms, et qu’il s’affiche dans la syntaxe .NET, avec un point comme l’opérateur de résolution de portée.

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>Exemple : les types valeur boxed

Types de valeur peuvent être utilisés avec la `GetType` ainsi de fonctionner, mais ils doivent tout d’abord être convertis.

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100; 
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>Exemple : typeid

Comme avec la `GetType` (méthode), la [typeid](../windows/typeid-cpp-component-extensions.md) opérateur retourne un pointeur vers un **Type** de l’objet, donc ce code indique le nom de type **System.Int32**. Affichage des noms de type est la fonctionnalité la plus élémentaire de la réflexion, mais une technique potentiellement plus utile consiste à inspecter ou découvrir les valeurs valides pour les types énumérés. Cela est possible à l’aide de la méthode statique **Enum::GetNames** de fonction, qui retourne un tableau de chaînes, chacune contenant une valeur d’énumération sous forme de texte.  L’exemple suivant récupère un tableau de chaînes qui décrit les valeurs d’énumération pour la **Options** enum (CLR) et les affiche dans une boucle.

Si une quatrième option est ajoutée à la **Options** énumération, ce code signalera la nouvelle option sans recompilation, même si l’énumération est définie dans un assembly distinct.

```cpp
// vcpp_reflection_3.cpp
// compile with: /clr
using namespace System;

enum class Options {   // not a native enum
   Option1, Option2, Option3
};

int main() {
   array<String^>^ names = Enum::GetNames(Options::typeid);

   Console::WriteLine("there are {0} options in enum '{1}'", 
               names->Length, Options::typeid);

   for (int i = 0 ; i < names->Length ; i++)
      Console::WriteLine("{0}: {1}", i, names[i]);

   Options o = Options::Option2;
   Console::WriteLine("value of 'o' is {0}", o);
}
```

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>Exemple : GetType membres et les propriétés

Le `GetType` objet prend en charge un nombre de membres et des propriétés qui peuvent être utilisées pour examiner un type. Ce code récupère et affiche certaines de ces informations :

```cpp
// vcpp_reflection_4.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine("type information for 'String':");
   Type ^ t = String::typeid;

   String ^ assemblyName = t->Assembly->FullName;
   Console::WriteLine("assembly name: {0}", assemblyName);

   String ^ nameSpace = t->Namespace;
   Console::WriteLine("namespace: {0}", nameSpace);

   String ^ baseType = t->BaseType->FullName;
   Console::WriteLine("base type: {0}", baseType);

   bool isArray = t->IsArray;
   Console::WriteLine("is array: {0}", isArray);

   bool isClass = t->IsClass;
   Console::WriteLine("is class: {0}", isClass);
}
```

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral, 
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>Exemple : l’énumération des types

La réflexion permet aussi l’énumération des types dans un assembly et les membres d’une classe. Pour illustrer cette fonctionnalité, définissez une classe simple :

```cpp
// vcpp_reflection_5.cpp
// compile with: /clr /LD
using namespace System;
public ref class TestClass {
   int m_i;
public:
   TestClass() {}
   void SimpleTestMember1() {}
   String ^ SimpleMember2(String ^ s) { return s; } 
   int TestMember(int i) { return i; }
   property int Member {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }
};
```

## <a name="example-inspection-of-assemblies"></a>Exemple : l’inspection des assemblys

Si le code ci-dessus est compilé dans une DLL appelée vcpp_reflection_6.dll, vous pouvez ensuite utiliser la réflexion pour inspecter le contenu de cet assembly. Cela implique l’utilisation de la fonction d’API de réflexion statique [Assembly::Load](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.load.aspx) pour charger l’assembly. Cette fonction retourne l’adresse d’un **Assembly** objet peut ensuite être interrogée sur les modules et les types dans.

Une fois le système de réflexion l’assembly, un tableau de **Type** objets est récupérée avec la [assembly.GetTypes](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.gettypes.aspx) (fonction). Chaque élément du tableau contient des informations sur un autre type, bien que dans ce cas, une seule classe soit définie. À l’aide d’une boucle, chaque **Type** dans ce tableau est interrogé sur les membres de type à l’aide de la **Type::GetMembers** (fonction). Cette fonction retourne un tableau de **MethodInfo** objets, chaque objet contenant des informations sur la fonction membre, un membre de données ou une propriété dans le type.

Notez que la liste de méthodes contient les fonctions explicitement définies dans **TestClass** et les fonctions héritent implicitement de la **System::Object** classe. En tant qu’elles sont décrites dans .NET plutôt que dans la syntaxe Visual C++, les propriétés s’affichent en tant que les données membres sous-jacentes auxquelles accèdent les fonctions get/set. Les fonctions get/set apparaissent dans cette liste en tant que méthodes régulières. Réflexion est prise en charge par le common language runtime, et non par le compilateur Visual C++.

Bien que vous avez utilisé ce code pour inspecter un assembly que vous avez définie, vous pouvez également utiliser ce code pour inspecter les assemblys .NET. Par exemple, si vous modifiez TestAssembly à mscorlib, puis vous verrez une liste de tous les types et méthodes définis dans mscorlib.dll.

```cpp
// vcpp_reflection_6.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;
using namespace System::Reflection;
int main() {
   Assembly ^ a = nullptr;
   try {
      // load assembly -- do not use file extension
      // will look for .dll extension first
      // then .exe with the filename
      a = Assembly::Load("vcpp_reflection_5");
   }
   catch (FileNotFoundException ^ e) {
      Console::WriteLine(e->Message);
      return -1;
   }

   Console::WriteLine("assembly info:");
   Console::WriteLine(a->FullName);
   array<Type^>^ typeArray = a->GetTypes();

   Console::WriteLine("type info ({0} types):", typeArray->Length);

   int totalTypes = 0;
   int totalMembers = 0;
   for (int i = 0 ; i < typeArray->Length ; i++) {
      // retrieve array of member descriptions
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();

      Console::WriteLine("  members of {0} ({1} members):", 
      typeArray[i]->FullName, member->Length);
      for (int j = 0 ; j < member->Length ; j++) {
         Console::Write("       ({0})", 
         member[j]->MemberType.ToString() );
         Console::Write("{0}  ", member[j]);
         Console::WriteLine("");
         totalMembers++;
      }
      totalTypes++;
   }
   Console::WriteLine("{0} total types, {1} total members",
   totalTypes, totalMembers);
}
```

## <a name="see-also"></a>Voir aussi

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
