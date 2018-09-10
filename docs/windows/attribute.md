---
title: attribut | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.attribute
dev_langs:
- C++
helpviewer_keywords:
- __typeof keyword
- custom attributes, creating
- attribute attribute
- attributes [C++/CLI], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54699888fc2988dd9b4ccec2a57b6d9df0d4e79e
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314771"
---
# <a name="attribute"></a>Attribut

Vous permet de créer un attribut personnalisé.

## <a name="syntax"></a>Syntaxe

```cpp
[ attribute(
   AllowOn,
   AllowMultiple=boolean,
   Inherited=boolean
) ]
```

### <a name="parameters"></a>Paramètres

*AllowOn*  
Spécifie les éléments de langage auquel l’attribut personnalisé peut être appliqué. Valeur par défaut est `System::AttributeTargets::All` (consultez [System::AttributeTargets](https://msdn.microsoft.com/library/system.attributetargets.aspx)).

*AllowMultiple*  
Spécifie si l’attribut personnalisé peut être appliqué à plusieurs reprises d’une construction. Valeur par défaut est FALSE.

*Héritée*  
Indique si l’attribut doit être héritées par les sous-classes. Le compilateur ne fournit aucune prise en charge spéciale pour cette fonctionnalité ; C’est le travail des consommateurs de l’attribut (`Reflection`, par exemple) afin de respecter ces informations. Si *Inherited* a la valeur TRUE, l’attribut est hérité. Si *AllowMultiple* a la valeur TRUE, l’attribut s’accumulent sur le membre dérivé ; si *AllowMultiple* est FALSE, l’attribut remplace (ou remplacez) dans l’héritage. Si *Inherited* est FALSE, l’attribut ne sera pas être hérité. Valeur par défaut est TRUE.

## <a name="remarks"></a>Notes

> [!NOTE]
> Le **attribut** attribute est maintenant déconseillé.  Utilisez l’attribut runtime de langage commun `System.Attribute` à directement pour créer des attirbutes défini par l’utilisateur. Pour plus d’informations, consultez [User-Defined Attributes](../windows/user-defined-attributes-cpp-component-extensions.md).

Vous définissez un [attribut personnalisé](../windows/custom-attributes-cpp.md) en plaçant le **attribut** attribut sur une définition de classe ou un struct managée. Le nom de la classe est l’attribut personnalisé. Exemple :

```cpp
[ attribute(Parameter) ]
public ref class MyAttr {};
```

définit un attribut appelé `MyAttr` qui peut être appliqué aux paramètres de fonction. La classe doit être publique si l’attribut doit être utilisé dans d’autres assemblys.

> [!NOTE]
> Pour éviter les collisions d’espace de noms, tous les noms d’attributs se terminent implicitement par « Attribute » ; Dans cet exemple, le nom de l’attribut et la classe est en fait `MyAttrAttribute`, mais `MyAttr` et `MyAttrAttribute` peuvent être utilisés indifféremment.

Les constructeurs publics de la classe définissent les paramètres sans nom de l’attribut. Constructeurs surchargés autoriser plusieurs façons de spécifier l’attribut, donc un attribut personnalisé qui est défini comme suit :

```cpp
// cpp_attr_ref_attribute.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]   // apply attribute to classes
public ref class MyAttr {
public:
   MyAttr() {}   // Constructor with no parameters
   MyAttr(int arg1) {}   // Constructor with one parameter
};

[MyAttr]
ref class ClassA {};   // Attribute with no parameters

[MyAttr(123)]
ref class ClassB {};   // Attribute with one parameter
```

Données membres publiques et les propriétés de la classe sont des paramètres nommés facultatif de l’attribut :

```cpp
// cpp_attr_ref_attribute_2.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class) ]
ref class MyAttr {
public:
   // Property Priority becomes attribute's named parameter Priority
    property int Priority {
       void set(int value) {}
       int get() { return 0;}
   }
   // Data member Version becomes attribute's named parameter Version
   int Version;
   MyAttr() {}   // constructor with no parameters
   MyAttr(int arg1) {}   // constructor with one parameter
};

[MyAttr(123, Version=2)]
ref class ClassC {};
```

Pour obtenir la liste des types de paramètre d’attribut possibles, consultez [attributs personnalisés](../windows/custom-attributes-cpp.md).

Consultez [User-Defined Attributes](../windows/user-defined-attributes-cpp-component-extensions.md) pour une discussion sur les cibles d’attribut.

Le **attribut** attribut a un *AllowMultiple* paramètre qui spécifie si l’attribut personnalisé est à usage unique ou multiuse (peut apparaître plusieurs fois sur la même entité).

```cpp
// cpp_attr_ref_attribute_3.cpp
// compile with: /c /clr
using namespace System;
[ attribute(AttributeTargets::Class, AllowMultiple = true) ]
ref struct MyAttr {
   MyAttr(){}
};   // MyAttr is a multiuse attribute

[MyAttr, MyAttr()]
ref class ClassA {};
```

Classes d’attributs personnalisés sont dérivées directement ou indirectement à partir de <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, ce qui permet d’identifier les définitions d’attributs dans les métadonnées rapidement et facilement. Le **attribut** attribut implique l’héritage à partir de `System::Attribute`, dérivation explicite n’est pas nécessaire :

```cpp
[ attribute(Class) ]
ref class MyAttr
```

est équivalent à

```cpp
[ attribute(Class) ]
ref class MyAttr : System::Attribute   // OK, but redundant.
```

**attribut** est un alias pour <xref:System.AttributeUsageAttribute?displayProperty=fullName> (pas AttributeAttribute ; il s’agit d’une exception à la règle d’affectation de noms d’attribut).

## <a name="requirements"></a>Configuration requise

### <a name="attribute-context"></a>Contexte d'attribut

|||
|-|-|
|**S'applique à**|**classe ref**, **un struct ref**|
|**Renouvelable**|Non|
|**Attributs requis**|Aucun.|
|**Attributs non valides**|Aucun.|

Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).

## <a name="example"></a>Exemple

```cpp
// cpp_attr_ref_attribute_4.cpp
// compile with: /c /clr
using namespace System;
[attribute(AttributeTargets::Class)]
ref struct ABC {
   ABC(Type ^) {}
};

[ABC(String::typeid)]   // typeid operator yields System::Type ^
ref class MyClass {};
```

## <a name="example"></a>Exemple

Le `Inherited` argument nommé Spécifie si un attribut personnalisé appliqué à une classe de base s’affichera sur la réflexion d’une classe dérivée.

```cpp
// cpp_attr_ref_attribute_5.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

[attribute( AttributeTargets::Method, Inherited=false )]
ref class BaseOnlyAttribute { };

[attribute( AttributeTargets::Method, Inherited=true )]
ref class DerivedTooAttribute { };

ref struct IBase {
public:
   [BaseOnly, DerivedToo]
   virtual void meth() {}
};

// Reflection on Derived::meth will show DerivedTooAttribute
// but not BaseOnlyAttribute.
ref class Derived : public IBase {
public:
   virtual void meth() override {}
};

int main() {
   IBase ^ pIB = gcnew Derived;

   MemberInfo ^ pMI = pIB->GetType( )->GetMethod( "meth" );
   array<Object ^> ^ pObjs = pMI->GetCustomAttributes( true );
   Console::WriteLine( pObjs->Length ) ;
}
```

```Output
2
```

## <a name="see-also"></a>Voir aussi

[Référence alphabétique des attributs](../windows/attributes-alphabetical-reference.md)  
