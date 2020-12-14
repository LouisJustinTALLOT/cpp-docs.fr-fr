---
description: 'En savoir plus sur : réflexion (C++/CLI)'
title: Réflexion (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: a3a9a33a239ec678279455ea41b7c60749cc0189
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245796"
---
# <a name="reflection-ccli"></a>Réflexion (C++/CLI)

La réflexion permet d’inspecter les types de données connus au moment de l’exécution. La réflexion permet l’énumération des types de données dans un assembly donné, et les membres d’une classe ou d’un type valeur donnés peuvent être découverts. Cela est vrai que le type soit connu ou référencé au moment de la compilation. Cela fait de la réflexion une fonctionnalité utile pour le développement et les outils de gestion du code.

Notez que le nom d’assembly fourni est le nom fort (consultez [création et utilisation d’assemblys Strong-Named](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), qui comprend la version, la culture et les informations de signature de l’assembly. Notez également que le nom de l’espace de noms dans lequel le type de données est défini peut être récupéré, ainsi que le nom de la classe de base.

La méthode la plus courante pour accéder aux fonctionnalités de réflexion consiste à utiliser la <xref:System.Object.GetType%2A> méthode. Cette méthode est fournie par <xref:System.Object?displayProperty=nameWithType> , à partir de laquelle dérivent toutes les classes récupérées par le garbage collector.

> [!NOTE]
> La réflexion sur un fichier. exe généré avec le compilateur Microsoft C++ est autorisée uniquement si le fichier. exe est généré avec les options de compilateur **/clr : pure** ou **/clr : safe** . Les options de compilateur **/clr : pure** et **/clr : safe** sont dépréciées dans Visual Studio 2015 et ne sont pas disponibles dans Visual Studio 2017. Pour plus d’informations [, consultez/CLR (compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) .

Pour plus d'informations, consultez <xref:System.Reflection>

## <a name="example-gettype"></a>Exemple : GetType

La `GetType` méthode retourne un pointeur vers un <xref:System.Type> objet de classe, qui décrit le type sur lequel l’objet est basé. (L’objet **type** ne contient pas d’informations spécifiques à l’instance.) L’un de ces éléments est le nom complet du type, qui peut être affiché comme suit :

Notez que le nom de type inclut la portée complète dans laquelle le type est défini, y compris l’espace de noms, et qu’il est affiché dans la syntaxe .NET, avec un point comme opérateur de résolution de portée.

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

## <a name="example-boxed-value-types"></a>Exemple : types valeur boxed

Les types valeur peuvent également être utilisés avec la `GetType` fonction, mais ils doivent tout d’abord être boxed.

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

Comme avec la `GetType` méthode, l’opérateur [typeid](../extensions/typeid-cpp-component-extensions.md) retourne un pointeur vers un objet de **type** , donc ce code indique le nom de type **System. Int32**. L’affichage des noms de types est la fonctionnalité de réflexion la plus simple, mais une technique potentiellement plus utile consiste à inspecter ou à découvrir les valeurs valides pour les types énumérés. Pour ce faire, vous pouvez utiliser la fonction static **enum :: GetNames** , qui retourne un tableau de chaînes, chacune contenant une valeur d’énumération sous forme de texte.  L’exemple suivant récupère un tableau de chaînes qui décrit les valeurs d’énumération de valeur pour l’énumération d' **options** (CLR) et les affiche dans une boucle.

Si une quatrième option est ajoutée à l’énumération **options** , ce code signale la nouvelle option sans recompilation, même si l’énumération est définie dans un assembly distinct.

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

## <a name="example-gettype-members-and-properties"></a>Exemple : membres et propriétés GetType

L' `GetType` objet prend en charge un certain nombre de membres et de propriétés qui peuvent être utilisés pour examiner un type. Ce code permet de récupérer et d’afficher certaines de ces informations :

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

## <a name="example-enumeration-of-types"></a>Exemple : énumération de types

La réflexion autorise également l’énumération des types dans un assembly et les membres au sein des classes. Pour illustrer cette fonctionnalité, définissez une classe simple :

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

## <a name="example-inspection-of-assemblies"></a>Exemple : inspection des assemblys

Si le code ci-dessus est compilé en une DLL appelée vcpp_reflection_6.dll, vous pouvez utiliser la réflexion pour inspecter le contenu de cet assembly. Cela implique l’utilisation de la fonction d’API de réflexion statique XREF : System. Reflection. assembly. Load% 2A ? displayProperty = nameWithType pour charger l’assembly. Cette fonction retourne l’adresse d’un objet **assembly** qui peut ensuite être interrogé à propos des modules et des types dans.

Une fois que le système de réflexion a chargé avec succès l’assembly, un tableau d’objets de **type** est récupéré avec la <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> fonction. Chaque élément de tableau contient des informations sur un type différent, même si, dans ce cas, une seule classe est définie. À l’aide d’une boucle, chaque **type** de ce tableau est interrogé sur les membres de type à l’aide de la fonction **type :: GetMembers** . Cette fonction retourne un tableau d’objets **MethodInfo** , chaque objet contenant des informations sur la fonction membre, le membre de données ou la propriété dans le type.

Notez que la liste des méthodes comprend les fonctions explicitement définies dans **TestClass** et les fonctions héritées implicitement de la classe **System :: Object** . Dans le cadre de la description dans .NET plutôt que dans la syntaxe Visual C++, les propriétés apparaissent en tant que membre de données sous-jacent accessible par les fonctions d’extraction/définition. Les fonctions d’extraction/définition apparaissent dans cette liste comme des méthodes normales. La réflexion est prise en charge par le common language runtime, et non par le compilateur Microsoft C++.

Bien que vous ayez utilisé ce code pour inspecter un assembly que vous avez défini, vous pouvez également utiliser ce code pour inspecter les assemblys .NET. Par exemple, si vous remplacez TestAssembly par mscorlib, vous verrez une liste de tous les types et méthodes définis dans mscorlib.dll.

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

## <a name="how-to-implement-a-plug-in-component-architecture-using-reflection"></a><a name="implement"></a> Comment : implémenter une architecture de composant Plug-In à l’aide de la réflexion

Les exemples de code suivants illustrent l’utilisation de la réflexion pour implémenter une architecture « plug-in » simple. La première liste est l’application, et la seconde est le plug-in. L’application est un formulaire à plusieurs documents qui se remplit à l’aide de toutes les classes basées sur des formulaires de la DLL de plug-in fournie en tant qu’argument de ligne de commande.

L’application tente de charger l’assembly fourni à l’aide de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> méthode. En cas de réussite, les types à l’intérieur de l’assembly sont énumérés à l’aide de la <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> méthode. La compatibilité de chaque type est ensuite vérifiée à l’aide de la <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> méthode. Dans cet exemple, les classes trouvées dans l’assembly fourni doivent être dérivées de la <xref:System.Windows.Forms.Form> classe pour être qualifiées de plug-in.

Les classes compatibles sont ensuite instanciées à l’aide de la <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> méthode, qui accepte un <xref:System.Type> comme argument et retourne un pointeur vers une nouvelle instance. Chaque nouvelle instance est ensuite attachée au formulaire et affichée.

Notez que la <xref:System.Reflection.Assembly.Load%2A> méthode n’accepte pas les noms d’assemblys qui incluent l’extension de fichier. La fonction main de l’application supprime toutes les extensions fournies, de sorte que l’exemple de code suivant fonctionne dans les deux cas.

### <a name="example"></a>Exemple

Le code suivant définit l’application qui accepte les plug-ins. Un nom d’assembly doit être fourni comme premier argument. Cet assembly doit contenir au moins un <xref:System.Windows.Forms.Form> type dérivé public.

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>Exemple

Le code suivant définit trois classes dérivées de <xref:System.Windows.Forms.Form> . Lorsque le nom de l’assembly résultant est passé au fichier exécutable dans la liste précédente, chacune de ces trois classes sera découverte et instanciée, bien qu’elles soient toutes inconnues de l’application d’hébergement au moment de la compilation.

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="how-to-enumerate-data-types-in-assemblies-using-reflection"></a><a name="enumerate"></a> Comment : énumérer des types de données dans des assemblys à l’aide de la réflexion

Le code suivant illustre l’énumération des types et des membres publics à l’aide de <xref:System.Reflection> .

À partir du nom d’un assembly, dans le répertoire local ou dans le GAC, le code ci-dessous tente d’ouvrir l’assembly et de récupérer les descriptions. En cas de réussite, chaque type est affiché avec ses membres publics.

Notez que <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> requiert l’utilisation d’une extension de fichier. Par conséquent, l’utilisation de « mscorlib.dll » comme argument de ligne de commande échoue, tandis que l’utilisation de « mscorlib » se traduira par l’affichage des types de .NET Framework. Si aucun nom d’assembly n’est fourni, le code détecte et signale les types dans l’assembly actuel (le fichier EXE qui résulte de ce code).

### <a name="example"></a>Exemple

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>Voir aussi

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
