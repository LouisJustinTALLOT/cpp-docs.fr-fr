---
title: attribut | Documents Microsoft
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
- attributes [C++], custom
ms.assetid: 8cb3489f-65c4-44ea-b0aa-3c3c6b15741d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9826b689e2b8a640efe66e8625b97b3cec347acf
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33862060"
---
# <a name="attribute"></a>Attribut
Vous permet de créer un attribut personnalisé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ attribute(  
   AllowOn,  
   AllowMultiple=boolean,  
   Inherited=boolean  
) ]  
```  
  
#### <a name="parameters"></a>Paramètres  
 *AllowOn*  
 Spécifie les éléments de langage auquel l’attribut personnalisé peut être appliqué. Valeur par défaut est **System::AttributeTargets::All** (consultez [System::AttributeTargets](https://msdn.microsoft.com/en-us/library/system.attributetargets.aspx)).  
  
 `AllowMultiple`  
 Spécifie si l’attribut personnalisé peut être appliqué plusieurs fois à une construction. Valeur par défaut est **FALSE**.  
  
 `Inherited`  
 Indique si l’attribut doit être héritées par les sous-classes. Le compilateur ne fournit aucune prise en charge spéciale pour cette fonctionnalité ; Il est le travail des consommateurs d’attribut (réflexion, par exemple) afin de respecter ces informations. Si `Inherited` est **TRUE**, l’attribut est hérité. Si `AllowMultiple` est **TRUE**, l’attribut s’accumulent sur le membre dérivé ; si `AllowMultiple` est **FALSE**, l’attribut remplace (ou remplacez) d’héritage. Si `Inherited` est **FALSE**, l’attribut ne sera pas être héritée. Valeur par défaut est **TRUE**.  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Le `attribute` attribut est désormais déconseillé.  Utilisez l’attribut common language runtime System.Attribute directement pour créer des attirbutes de défini par l’utilisateur.  Pour plus d’informations, consultez [les attributs définis par l’utilisateur](../windows/user-defined-attributes-cpp-component-extensions.md).  
  
 Vous définissez un [attribut personnalisé](../windows/custom-attributes-cpp.md) en plaçant le `attribute` attribut sur une définition de classe ou une structure managée. Le nom de la classe est l’attribut personnalisé. Par exemple :  
  
```  
[ attribute(Parameter) ]  
public ref class MyAttr {};  
```  
  
 définit un attribut appelé MyAttr qui peut être appliqué aux paramètres de fonction. La classe doit être publique si l’attribut doit être utilisé dans d’autres assemblys.  
  
> [!NOTE]
>  Pour éviter les collisions d’espace de noms, tous les noms d’attributs se terminent implicitement par « Attribute » ; Dans cet exemple, le nom de l’attribut et la classe est en fait MyAttrAttribute mais MyAttr et MyAttrAttribute peuvent être utilisées indifféremment.  
  
 Constructeurs publics de la classe définissent les paramètres sans nom de l’attribut. Constructeurs surchargés autoriser plusieurs méthodes pour spécifier l’attribut, donc un attribut personnalisé est défini comme suit :  
  
```  
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
  
 Membres de données publics et les propriétés de la classe sont des paramètres nommés de l’attribut facultatif :  
  
```  
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
  
 Pour obtenir la liste des types de paramètres d’attribut possibles, consultez [attributs personnalisés](../windows/custom-attributes-cpp.md).  
  
 Consultez [les attributs définis par l’utilisateur](../windows/user-defined-attributes-cpp-component-extensions.md) pour en savoir plus sur les cibles d’attribut.  
  
 Le `attribute` attribut a un `AllowMultiple` paramètre qui spécifie si l’attribut personnalisé est à usage unique ou multiuse (peut apparaître plusieurs fois sur la même entité).  
  
```  
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
  
 Classes d’attributs personnalisés sont dérivés directement ou indirectement <xref:System.ComponentModel.AttributeCollection.%23ctor%2A>, qui permet d’identifier les définitions d’attributs dans les métadonnées rapidement et facilement. Le `attribute` attribut implique l’héritage de System::Attribute, dérivation explicite n’est pas nécessaire :  
  
```  
[ attribute(Class) ]  
ref class MyAttr  
```  
  
 est équivalent à  
  
```  
[ attribute(Class) ]  
ref class MyAttr : System::Attribute   // OK, but redundant.  
```  
  
 `attribute` est un alias de <xref:System.AttributeUsageAttribute?displayProperty=fullName> (pas attributAttribute ; il s’agit d’une exception à la règle d’affectation de noms d’attribut).  
  
## <a name="requirements"></a>Spécifications  
  
### <a name="attribute-context"></a>Contexte d'attribut  
  
|||  
|-|-|  
|**S'applique à**|`ref` **classe**, **un struct ref**|  
|**Renouvelable**|Non|  
|**Attributs requis**|Aucun|  
|**Attributs non valides**|Aucun|  
  
 Pour plus d'informations sur les contextes d'attribut, consultez [Contextes d'attribut](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Exemple  
  
```  
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
 Le `Inherited` argument nommé Spécifie si un attribut personnalisé est appliqué à une classe de base s’afficheront sur la réflexion d’une classe dérivée.  
  
```  
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
 [Attributs personnalisés](http://msdn.microsoft.com/en-us/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)