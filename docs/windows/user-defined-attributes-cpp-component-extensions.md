---
title: Attributs définis par l’utilisateur (C++ / c++ / CLI et c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: f64cf5415e79678f0e0b43b58aae2249601fb3d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546651"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Attributs définis par l’utilisateur (C++ / c++ / CLI et c++ / CX)

C++ / c++ / CLI et c++ / CX permettent de créer des attributs spécifiques à la plateforme qui étendent les métadonnées d’une interface, classe ou structure, méthode, paramètre ou énumération. Ces attributs sont distincts de la [des attributs C++ standards](../cpp/attributes.md).

## <a name="windows-runtime"></a>Windows Runtime

Vous pouvez appliquer C + c++ / attributs CX aux propriétés, mais pas de constructeurs ou méthodes.

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Les informations et la syntaxe présentée dans cette rubrique est destiné à remplacer les informations présentées dans [attribut](attributes/attribute.md).

Vous pouvez définir un attribut personnalisé en définissant un type et en rendant <xref:System.Attribute> une classe de base pour le type et éventuellement appliquer la <xref:System.AttributeUsageAttribute> attribut.

Pour plus d'informations, voir :

- [Cibles d’attribut](attribute-targets-cpp-component-extensions.md)

- [Types de paramètre d’attribut](attribute-parameter-types-cpp-component-extensions.md)

Pour plus d’informations sur la signature d’assemblys dans Visual C++, consultez [les assemblys de nom fort (signature d’Assembly) (C++ / c++ / CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Configuration requise

Option du compilateur : `/clr`

### <a name="examples"></a>Exemples

L’exemple suivant montre comment définir un attribut personnalisé.

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

L’exemple suivant illustre certaines fonctionnalités importantes d’attributs personnalisés. Par exemple, cet exemple montre une utilisation courante des attributs personnalisés : l’instanciation d’un serveur qui peut se décrire complètement aux clients.

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

Le `Object^` type remplace le type de données variant. L’exemple suivant définit un attribut personnalisé qui prend un tableau de `Object^` en tant que paramètres.

Arguments d’attribut doivent être des constantes de compilation ; dans la plupart des cas, ils doivent être des littéraux constants.

Consultez [typeid](typeid-cpp-component-extensions.md) pour plus d’informations sur la façon de retourner une valeur de System::Type d’un bloc d’attributs personnalisés.

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

Le runtime nécessite que la partie publique de la classe d’attributs personnalisés doit être sérialisable.  Lors de la création d’attributs personnalisés, les arguments nommés de l’attribut personnalisé sont limités à des constantes de compilation.  (La considérer comme une séquence de bits ajoutés à votre disposition de classe dans les métadonnées.)

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>Voir aussi

[Extensions de composants pour .NET et UWP](component-extensions-for-runtime-platforms.md)