---
description: 'En savoir plus sur les attributs suivants : User-Defined (C++/CLI et C++/CX)'
title: Attributs définis par l’utilisateur (C++/CLI et C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: 2fab2cc1317522b43cd4bddbb56ae174907607d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327900"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>Attributs définis par l’utilisateur (C++/CLI et C++/CX)

C++/CLI et C++/CX permettent de créer des attributs spécifiques à la plateforme qui étendent les métadonnées d’une interface, d’une classe ou structure, d’une méthode, d’un paramètre ou d’une énumération. Ces attributs sont différents des [attributs C++ standard](../cpp/attributes.md).

## <a name="windows-runtime"></a>Windows Runtime

Vous pouvez appliquer des attributs C++/CX aux propriétés, mais pas aux constructeurs ou aux méthodes.

### <a name="requirements"></a>Spécifications

Option du compilateur : `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Les informations et la syntaxe présentées dans cette rubrique doivent remplacer les informations présentées dans [Attributs](../windows/attributes/attribute.md).

Vous pouvez définir un attribut personnalisé en définissant un type, en faisant de <xref:System.Attribute> une classe de base pour le type, et en appliquant éventuellement l’attribut <xref:System.AttributeUsageAttribute>.

Pour plus d'informations, consultez les pages suivantes :

- [Cibles d’attribut](attribute-targets-cpp-component-extensions.md)

- [Types de paramètres d’attribut](attribute-parameter-types-cpp-component-extensions.md)

Pour plus d’informations sur la signature d’assemblys dans Visual C++, consultez [Assemblys de nom fort (signature d’assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

### <a name="requirements"></a>Spécifications

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

L’exemple suivant illustre certaines fonctionnalités importantes des attributs personnalisés. Par exemple, l’exemple suivant montre une utilisation courante des attributs personnalisés : l’instanciation d’un serveur qui peut se décrire complètement aux clients.

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

Le type `Object^` remplace le type de données variant. L’exemple suivant définit un attribut personnalisé qui prend un tableau de `Object^` en tant que paramètres.

Les arguments d’attributs doivent être des constantes au moment de la compilation. Dans la plupart des cas, ils doivent être des littéraux constants.

Consultez [typeid](typeid-cpp-component-extensions.md) pour plus d’informations sur la manière de retourner une valeur System::Type depuis un bloc d’attributs personnalisés.

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

Le runtime nécessite que la partie publique de la classe d’attributs personnalisés soit sérialisable.  Lors de la création d’attributs personnalisés, les arguments nommés de l’attribut personnalisé sont limités aux constantes au moment de la compilation.  (Il s’agit d’une séquence de bits ajoutée à votre disposition de classe dans les métadonnées.)

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

[Extensions de composant pour .NET et UWP](component-extensions-for-runtime-platforms.md)
