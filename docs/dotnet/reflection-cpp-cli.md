---
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
ms.openlocfilehash: a17910e0288b81723aa837ba9204bb40713d5d49
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770795"
---
# <a name="reflection-ccli"></a>Réflexion (C++/CLI)

La réflexion permet d’inspecter lors de l’exécution des types de données connues. La réflexion permet l’énumération des types de données dans un assembly donné, et les membres d’un type valeur ou classe donné peuvent être découverts. Cela est vrai que le type a été appelé ou référencé au moment de la compilation. C’est donc une fonctionnalité utile pour le développement et les outils de gestion de code.

Notez que le nom de l’assembly fourni est le nom fort (consultez [création et assemblys avec nom fort](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)), qui inclut la version de l’assembly, de culture et les informations de signature. Notez également que le nom de l’espace de noms dans lequel le type de données est défini peut être extraits, ainsi que le nom de la classe de base.

La méthode la plus courante pour accéder aux fonctionnalités de réflexion consiste à utiliser le <xref:System.Object.GetType%2A> (méthode). Cette méthode est fournie par <xref:System.Object?displayProperty=nameWithType>, à partir de laquelle dérivent toutes les classes de garbage collection.

> [!NOTE]
> Réflexion sur un .exe générées avec le compilateur Visual C++ est uniquement autorisée si le fichier .exe est générée avec le **/CLR : pure** ou **/CLR : safe** options du compilateur. Le **/CLR : pure** et **/CLR : safe** options du compilateur sont déconseillées dans Visual Studio 2015 et non disponible dans Visual Studio 2017. Consultez [/clr (Compilation pour le Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) pour plus d’informations.

Pour plus d'informations, consultez <xref:System.Reflection>

## <a name="example-gettype"></a>Exemple : GetType

Le `GetType` méthode retourne un pointeur vers un <xref:System.Type> objet de classe, qui décrit le type sur lorsque l’objet est basé. (Le **Type** objet ne contient pas toutes les informations spécifiques à l’instance.) Un de ces éléments est le nom complet du type, qui peut être affiché comme suit :

Notez que le nom du type inclut toute la portée dans laquelle le type est défini, y compris l’espace de noms, et qu’elle est affichée dans la syntaxe de .NET, avec un point comme l’opérateur de résolution de portée.

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

Types de valeur peuvent être utilisés avec la `GetType` fonctionnent également, mais ils doivent tout d’abord être convertis.

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

Comme avec la `GetType` (méthode), le [typeid](../extensions/typeid-cpp-component-extensions.md) opérateur retourne un pointeur vers un **Type** de l’objet, donc ce code indique le nom de type **System.Int32**. Affichage des noms de type est la fonctionnalité la plus élémentaire de la réflexion, mais une technique potentiellement plus utile consiste à inspecter ou découvrir les valeurs valides pour les types énumérés. Cela est possible à l’aide de la méthode statique **Enum::GetNames** fonction, qui retourne un tableau de chaînes, chacune contenant une valeur d’énumération sous forme de texte.  L’exemple suivant récupère un tableau de chaînes qui décrit les valeurs d’énumération de valeur pour le **Options** enum (CLR) et les affiche dans une boucle.

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

## <a name="example-gettype-members-and-properties"></a>Exemple : Propriétés et membres de GetType

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

La réflexion permet également l’énumération des types dans un assembly et les membres dans les classes. Pour illustrer cette fonctionnalité, définissez une classe simple :

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

Si le code ci-dessus est compilé dans une DLL appelée vcpp_reflection_6.dll, vous pouvez ensuite utiliser la réflexion pour inspecter le contenu de cet assembly. Cela implique l’utilisation de la réflexion statique API fonction xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType pour charger l’assembly. Cette fonction retourne l’adresse d’un **Assembly** objet peut ensuite être interrogée sur les modules et les types dans.

Une fois le système de réflexion l’assembly, un tableau de **Type** objets est récupérée avec la <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType> (fonction). Chaque élément du tableau contient des informations sur un autre type, bien que dans ce cas, une seule classe est définie. À l’aide d’une boucle, chaque **Type** dans ce tableau est interrogé sur les membres de type à l’aide de la **Type::GetMembers** (fonction). Cette fonction retourne un tableau de **MethodInfo** objets, chaque objet contenant des informations sur la fonction membre, le membre de données ou la propriété dans le type.

Notez que la liste des méthodes inclut les fonctions explicitement définies dans **TestClass** et les fonctions héritent implicitement de la **System::Object** classe. En tant qu’elles sont décrites dans .NET plutôt que de la syntaxe Visual C++, les propriétés s’affichent en tant que les données membres sous-jacentes auxquelles accédé les fonctions get/set. Les fonctions get/set apparaissent dans cette liste en tant que méthodes régulières. La réflexion est prise en charge par le common language runtime, pas par le compilateur Visual C++.

Bien que vous avez utilisé ce code pour inspecter un assembly que vous avez définie, vous pouvez également utiliser ce code pour inspecter les assemblys .NET. Par exemple, si vous modifiez TestAssembly à mscorlib, puis vous verrez une liste de chaque type et une méthode définie dans mscorlib.dll.

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

## <a name="implement"></a> Guide pratique pour Implémenter une Architecture de composants plug-in à l’aide de la réflexion

Les exemples de code suivants illustrent l’utilisation de la réflexion pour implémenter une architecture de « plug-in » simple. La première liste correspond à l’application, et le second est le plug-in. L’application est un formulaire multidocument qui se remplit automatiquement à l’aide de toutes les classes en fonction du formulaire trouvés dans la DLL de plug-in fournie comme un argument de ligne de commande.

L’application tente de charger l’assembly fourni à l’aide de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> (méthode). Réussite, les types à l’intérieur de l’assembly sont énumérées à l’aide de la <xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName> (méthode). Ensuite, chaque type est vérifiée pour la compatibilité à l’aide du <xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName> (méthode). Dans cet exemple, les classes figurant dans l’assembly fourni doivent être dérivées de la <xref:System.Windows.Forms.Form> classe pour être considérée comme un plug-in.

Les classes compatibles sont alors instanciées avec le <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> (méthode), qui accepte un <xref:System.Type> en tant qu’argument et retourne un pointeur vers une nouvelle instance. Chaque nouvelle instance est ensuite attaché au formulaire et affiché.

Notez que le <xref:System.Reflection.Assembly.Load%2A> méthode n’accepte pas les noms d’assemblys qui incluent l’extension de fichier. La fonction principale de l’application supprime toute extension fournie pour l’exemple de code suivant fonctionne dans les deux cas.

### <a name="example"></a>Exemple

Le code suivant définit l’application qui accepte des plug-ins. Un nom d’assembly doit être fourni comme premier argument. Cet assembly doit contenir au moins un public <xref:System.Windows.Forms.Form> type dérivé.

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

Le code suivant définit trois classes dérivées de <xref:System.Windows.Forms.Form>. Lorsque le nom de l’assembly résultant est transmis à l’exécutable dans la liste précédente, chacune de ces trois classes sera découvert et instancié, en dépit du fait qu’elles étaient toutes inconnues de l’application d’hébergement au moment de la compilation.

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

## <a name="enumerate"></a> Guide pratique pour Énumérer des Types de données dans les assemblys à l’aide de la réflexion

Le code suivant illustre l’énumération de types publics et des membres à l’aide de <xref:System.Reflection>.

Étant donné le nom d’un assembly, dans le répertoire local ou dans le GAC, le code ci-dessous tente d’ouvrir l’assembly et de récupérer les descriptions. En cas de réussite, chaque type est affiché avec ses membres publics.

Notez que <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> exige qu’aucune extension de fichier n’est utilisée. Par conséquent, à l’aide de « mscorlib.dll » comme un argument de ligne de commande échoue, tandis que l’utilisation de simplement « mscorlib » entraîne l’affichage des types .NET Framework. Si aucun nom de l’assembly n’est fourni, le code sera détectent et signalent les types dans l’assembly actuel (le fichier EXE résultant de ce code).

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

- [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
