---
title: "Generic Interfaces (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic interfaces"
  - "interfaces, generic [C++}"
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Generic Interfaces (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Les restrictions applicables aux paramètres de type dans les classes sont les mêmes que celles qui s'appliquent aux paramètres de type dans les interfaces \(voir à [Generic Classes \(C\+\+\/CLI\)](../windows/generic-classes-cpp-cli.md)\).  
  
 Les règles qui contrôlent la surcharge de fonction sont les mêmes pour les fonctions ayant des classes génériques ou des interfaces génériques.  
  
 Les implémentations explicites de membre de l'interface fonctionnent avec les types d'interface construits de la même façon qu'avec les types d'interface simple \(consultez les exemples ci\-dessous\).  
  
 Pour plus d'informations sur les interfaces, consultez [interface class](../windows/interface-class-cpp-component-extensions.md).  
  
## Syntaxe  
  
```  
[attributes] generic <class-key type-parameter-identifier[, ...]>  
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;  
```  
  
## Notes  
 *Attribut* \(facultatif\).  
 Les informations supplémentaires déclarative.  Pour plus d'informations sur les attributs et les classes d'attributs, consultez la section attributs.  
  
 *class\-key*  
 **classe** ou **nom de type**  
  
 `type-parameter-identifier(s)`  
 Liste séparée par des virgules des identificateurs.  
  
 `type-parameter-constraints-clauses`  
 Le format spécifié dans [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *Accessibility\- modificateurs* \(facultatif\)  
 Modificateurs d'Accessibilité \(par exemple  **public, private**\).  
  
 *identificateur*  
 Le nom de l'interface.  
  
 *base liste* \(facultatif\)  
 Liste qui contient un ou plusieurs interfaces de base explicites séparés par des virgules.  
  
 *interface\-corps*  
 Déclarations des membres de l'interface.  
  
 *déclarateurs* \(facultatif\)  
 Déclarations de variables en fonction de ce type.  
  
## Exemple  
 L'exemple suivant indique comment déclarer et instancier une interface générique.  Dans l'exemple, l'interface générique `IList<ItemType>` est déclarée.  Elle est ensuite mise en œuvre par deux classes génériques, `List1<ItemType>` et `List2<ItemType>`, avec des implémentations différentes.  
  
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
  
  **Liste liée**  
**Liste1**  
**Liste de tables**  
**Liste2**   
## Exemple  
 L'exemple suivant déclare une interface générique, `IMyGenIface`, et deux interfaces, `IMySpecializedInt` et `ImySpecializedString`génériques, qui spécialisent `IMyGenIface`.  Les deux interfaces spécialisées sont ensuite implémentées par deux classes, `MyIntClass` et `MyStringClass`.  L'exemple montre comment spécialiser les interfaces génériques, le générique d'instancier des interfaces génériques, et appelle les membres explicitement implémentés dans les interfaces.  
  
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
  
  **La zone entière contient : 1234**  
**Le champ de chaîne contient : Ma chaîne**   
## Voir aussi  
 [Generics](../windows/generics-cpp-component-extensions.md)