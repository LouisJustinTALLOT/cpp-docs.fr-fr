---
title: "Interfaces génériques (Visual C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6b41ce8b1affe36126a7b36bea631880d13fdeff
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="generic-interfaces-visual-c"></a>Interfaces génériques (Visual C++)
Les restrictions qui s’appliquent aux paramètres de type sur les classes sont les mêmes que celles qui s’appliquent aux paramètres de type sur les interfaces (consultez [Classes génériques (C + c++ / CLI)](../windows/generic-classes-cpp-cli.md)).  
  
 Les règles qui contrôlent la surcharge de fonction sont les mêmes pour les fonctions dans les classes génériques ou les interfaces génériques.  
  
 Implémentations de membres d’interface explicite fonctionnent avec les types interface construits dans la même façon que les types interface simple (voir les exemples suivants).  
  
 Pour plus d’informations sur les interfaces, consultez [classe d’interface](../windows/interface-class-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[attributes] generic <class-key type-parameter-identifier[, ...]>  
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;  
```  
  
## <a name="remarks"></a>Remarques  
 *attributs* (facultatif)  
 Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et classes d’attributs, consultez attributs.  
  
 *clé de la classe*  
 **classe** ou **typename**  
  
 `type-parameter-identifier(s)`  
 Liste d’identificateurs séparés par des virgules.  
  
 `type-parameter-constraints-clauses`  
 Le format spécifié dans [contraintes sur les paramètres de Type générique (C + c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *modificateurs d’accessibilité* (facultatif)  
 Les modificateurs d’accessibilité (par exemple, **public, privé**).  
  
 *identifier*  
 Le nom de l’interface.  
  
 *base-list* (facultatif)  
 Une liste qui contient un ou plusieurs interfaces de base explicites séparés par des virgules.  
  
 *corps de l’interface*  
 Déclarations des membres d’interface.  
  
 *déclarateurs* (facultatif)  
 Déclarations de variables en fonction de ce type.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer et instancier une interface générique. Dans l’exemple, l’interface générique `IList<ItemType>` est déclarée. Il est ensuite implémentée par deux classes génériques, `List1<ItemType>` et `List2<ItemType>`, avec des implémentations différentes.  
  
```  
// generic_interface.cpp  
// compile with: /clr  
using namespace System;  
  
// An exception to be thrown by the List when  
// attempting to access elements beyond the  
// end of the list.  
ref class ElementNotFoundException : Exception {};  
  
// A generic List interface  
generic <typename ItemType>  
public interface class IList {  
   ItemType MoveFirst();  
   bool Add(ItemType item);  
   bool AtEnd();  
   ItemType Current();  
   void MoveNext();  
};  
  
// A linked list implementation of IList  
generic <typename ItemType>  
public ref class List1 : public IList<ItemType> {  
   ref class Node {  
      ItemType m_item;  
  
   public:  
      ItemType get_Item() { return m_item; };  
      void set_Item(ItemType value) { m_item = value; };  
  
      Node^ next;  
  
      Node(ItemType item) {  
         m_item = item;  
         next = nullptr;  
      }  
   };  
  
   Node^ first;  
   Node^ last;  
   Node^ current;  
  
   public:  
   List1() {  
      first = nullptr;  
      last = first;  
      current = first;  
   }  
  
   virtual ItemType MoveFirst() {  
      current = first;  
      if (first != nullptr)  
        return first->get_Item();  
      else  
         return ItemType();  
   }  
  
   virtual bool Add(ItemType item) {  
      if (last != nullptr) {   
         last->next = gcnew Node(item);  
         last = last->next;  
      }  
      else {  
         first = gcnew Node(item);  
         last = first;  
         current = first;  
      }  
      return true;  
   }  
  
   virtual bool AtEnd() {  
      if (current == nullptr )  
        return true;  
      else   
        return false;  
   }  
  
   virtual ItemType Current() {  
       if (current != nullptr)  
         return current->get_Item();  
       else  
         throw gcnew ElementNotFoundException();  
   }  
  
   virtual void MoveNext() {  
      if (current != nullptr)  
       current = current->next;  
      else  
        throw gcnew ElementNotFoundException();  
   }  
};  
  
// An array implementation of IList  
generic <typename ItemType>  
ref class List2 : public IList<ItemType> {  
   array<ItemType>^ item_array;  
   int count;  
   int current;  
  
   public:  
  
   List2() {  
      // not yet possible to declare an  
      // array of a generic type parameter  
      item_array = gcnew array<ItemType>(256);  
      count = current = 0;  
   }  
  
   virtual ItemType MoveFirst() {  
      current = 0;  
      return item_array[0];  
   }  
  
   virtual bool Add(ItemType item) {  
      if (count < 256)  
         item_array[count++] = item;  
      else  
        return false;  
      return true;  
   }  
  
   virtual bool AtEnd() {  
      if (current >= count)  
        return true;  
      else  
        return false;  
   }  
  
   virtual ItemType Current() {  
      if (current < count)  
        return item_array[current];  
      else  
        throw gcnew ElementNotFoundException();  
   }  
  
   virtual void MoveNext() {  
      if (current < count)   
         ++current;  
      else  
         throw gcnew ElementNotFoundException();  
   }  
};  
  
// Add elements to the list and display them.  
generic <typename ItemType>  
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {  
   list->Add(item1);  
   list->Add(item2);  
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())  
     Console::WriteLine(list->Current());  
}  
  
int main() {  
   // Instantiate both types of list.  
  
   List1<String^>^ list1 = gcnew List1<String^>();  
   List2<String^>^ list2 = gcnew List2<String^>();  
  
   // Use the linked list implementation of IList.  
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");  
  
   // Use the array implementation of the IList.  
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");  
}  
```  
  
```Output  
Linked List  
List1  
Array List  
List2  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple déclare une interface générique, `IMyGenIface`et deux interfaces non génériques, `IMySpecializedInt` et `ImySpecializedString`, spécialisés `IMyGenIface`. Les deux interfaces spécialisées sont ensuite implémentées par deux classes, `MyIntClass` et `MyStringClass`. L’exemple montre comment spécialiser des interfaces génériques, instancier des interfaces génériques et non génériques et appeler les membres implémentés explicitement sur les interfaces.  
  
```  
// generic_interface2.cpp  
// compile with: /clr  
// Specializing and implementing generic interfaces.  
using namespace System;  
  
generic <class ItemType>  
public interface class IMyGenIface {  
   void Initialize(ItemType f);  
};  
  
public interface class IMySpecializedInt: public IMyGenIface<int> {  
   void Display();  
};  
  
public interface class IMySpecializedString: public IMyGenIface<String^> {  
   void Display();  
};  
  
public ref class MyIntClass: public IMySpecializedInt {  
   int myField;  
  
public:   
   virtual void Initialize(int f) {  
      myField = f;  
   }  
  
   virtual void Display() {  
      Console::WriteLine("The integer field contains: {0}", myField);  
   }      
};  
  
public ref struct MyStringClass: IMySpecializedString {      
   String^ myField;  
  
public:  
   virtual void Initialize(String^ f) {  
      myField = f;  
    }  
  
   virtual void Display() {  
      Console::WriteLine("The String field contains: {0}", myField);  
   }  
};  
  
int main() {  
   // Instantiate the generic interface.  
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();  
  
   // Instantiate the specialized interface "IMySpecializedInt."  
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;  
  
   // Instantiate the generic interface.  
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();  
  
   // Instantiate the specialized interface "IMySpecializedString."  
   IMySpecializedString^ mySpStringObj =   
            (IMySpecializedString^) myStringObj;  
  
   // Call the explicitly implemented interface members.  
   myIntObj->Initialize(1234);  
   mySpIntObj->Display();  
  
   myStringObj->Initialize("My string");  
   mySpStringObj->Display();  
}  
```  
  
```Output  
The integer field contains: 1234  
The String field contains: My string  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](../windows/generics-cpp-component-extensions.md)