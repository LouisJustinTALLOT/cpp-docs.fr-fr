---
title: classe (C++) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- class_cpp
dev_langs:
- CPP
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ed344d5c15e709b09b760dee74a986dde6383d22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="class-c"></a>class (C++)
Le `class` mot clé déclare un type de classe ou définit un objet d’un type de classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [template-spec]  
       class [ms-decl-spec] [tag [: base-list ]]  
{  
   member-list  
} [declarators];  
[ class ] tag declarators;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `template-spec`  
 Spécifications de modèle facultatives. Pour plus d’informations, reportez-vous à [modèles](templates-cpp.md).  
  
 `class`  
 Mot clé `class`.  
  
 `ms-decl-spec`  
 Spécification de classe de stockage facultative. Pour plus d’informations, reportez-vous à la [__declspec](../cpp/declspec.md) (mot clé).  
  
 `tag`  
 Nom de type donné à la classe. La balise devient un mot réservé dans la portée de la classe. La balise est facultative. Si omis, une classe anonyme est définie. Pour plus d’informations, consultez [des Types de classe anonymes](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 Liste facultative des classes ou structures que dérive ses membres de cette classe. Consultez [des Classes de Base](../cpp/base-classes.md) pour plus d’informations. Chaque nom de classe ou une structure de base peut être précédée d’un spécificateur d’accès ([public](../cpp/public-cpp.md), [privé](../cpp/private-cpp.md), [protégé](../cpp/protected-cpp.md)) et le [virtuels](../cpp/virtual-cpp.md) mot clé. Consultez le tableau de l’accès aux membres dans [contrôle de l’accès aux membres de classe](member-access-control-cpp.md) pour plus d’informations.  
  
 `member-list`  
 Liste des membres de classe. Reportez-vous à [vue d’ensemble des membres de classe](../cpp/class-member-overview.md) pour plus d’informations.  
  
 `declarators`  
 Liste des déclarateurs spécifiant les noms d’une ou plusieurs instances du type de classe. Les déclarateurs peuvent inclure des listes d'initialiseurs si toutes les données membres de la classe sont `public`. Il s’agit plus courant dans les structures de données dont les membres sont `public` par défaut, que dans les classes. Consultez [vue d’ensemble des déclarateurs](../cpp/overview-of-declarators.md) pour plus d’informations.  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les classes en général, consultez une des rubriques suivantes :  
  
-   [struct](../cpp/struct-cpp.md)  
  
-   [union](../cpp/unions.md)  
  
-   [__multiple_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__single_inheritance](../cpp/inheritance-keywords.md)  
  
-   [__virtual_inheritance](../cpp/inheritance-keywords.md)  
  
 Pour plus d’informations sur les classes et structs, consultez [les Classes et Structs](../windows/classes-and-structs-cpp-component-extensions.md)  
  
## <a name="example"></a>Exemple  
  
```  
// class.cpp  
// compile with: /EHsc  
// Example of the class keyword  
// Exhibits polymorphism/virtual functions.  
  
#include <iostream>  
#include <string>  
#define TRUE = 1  
using namespace std;  
  
class dog  
{  
public:  
   dog()  
   {  
      _legs = 4;  
      _bark = true;  
   }  
  
   void setDogSize(string dogSize)  
   {  
      _dogSize = dogSize;  
   }  
   virtual void setEars(string type)      // virtual function  
   {  
      _earType = type;  
   }  
  
private:  
   string _dogSize, _earType;  
   int _legs;  
   bool _bark;  
  
};  
  
class breed : public dog  
{  
public:  
   breed( string color, string size)  
   {  
      _color = color;  
      setDogSize(size);  
   }  
  
   string getColor()  
   {  
      return _color;  
   }  
  
   // virtual function redefined  
   void setEars(string length, string type)  
   {  
      _earLength = length;  
      _earType = type;  
   }  
  
protected:  
   string _color, _earLength, _earType;  
};  
  
int main()  
{  
   dog mongrel;  
   breed labrador("yellow", "large");  
   mongrel.setEars("pointy");  
   labrador.setEars("long", "floppy");  
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)   
 [Classes et structs](../cpp/classes-and-structs-cpp.md)