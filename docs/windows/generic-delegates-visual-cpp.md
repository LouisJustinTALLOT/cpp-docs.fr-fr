---
title: Délégués génériques (Visual C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ecbfebc49f76eee7bb753af3d07052d1e05d73be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875596"
---
# <a name="generic-delegates-visual-c"></a>Délégués génériques (Visual C++)
Vous pouvez utiliser les paramètres de type générique avec des délégués. Pour plus d’informations sur les délégués, consultez [delegate (Extensions du composant C++)](../windows/delegate-cpp-component-extensions.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[attributes]   
generic < [class | typename] type-parameter-identifiers>  
[type-parameter-constraints-clauses]  
[accessibility-modifiers] delegate result-type identifier   
([formal-parameters]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `attributes` (Facultatif)  
 Informations déclaratives supplémentaires. Pour plus d’informations sur les attributs et classes d’attributs, consultez attributs.  
  
 *type-paramètre-identificateur (s)*  
 Liste de séparées par des virgules d’identificateurs pour les paramètres de type.  
  
 `type-parameter-constraints-clauses`  
 Le format spécifié dans [contraintes sur les paramètres de Type générique (C + c++ / CLI)](../windows/constraints-on-generic-type-parameters-cpp-cli.md)  
  
 *modificateurs d’accessibilité* (facultatif)  
 Les modificateurs d’accessibilité (par exemple, **public**, `private`).  
  
 *result-type*  
 Le type de retour du délégué.  
  
 *identifier*  
 Le nom du délégué.  
  
 *paramètres formels* (facultatif)  
 La liste de paramètres du délégué.  
  
## <a name="example"></a>Exemple  
 Les paramètres de type de délégué sont spécifiés au point où un objet de délégué est créé. Le délégué et la méthode associée doivent avoir la même signature. Voici un exemple d’une déclaration de délégué générique.  
  
```  
// generics_generic_delegate1.cpp  
// compile with: /clr /c  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre que  
  
-   Vous ne pouvez pas utiliser le même objet de délégué avec différents types construits. Permet de créer des objets pour différents types de délégué différents.  
  
-   Un délégué générique peut être associé à une méthode générique.  
  
-   Lorsqu’une méthode générique est appelée sans spécifier les arguments de type, le compilateur tente de déduire les arguments de type pour l’appel.  
  
```  
// generics_generic_delegate2.cpp  
// compile with: /clr  
generic <class ItemType>  
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);  
  
generic <class ItemType>  
ref struct MyGenClass {  
   ItemType MyMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
ref struct MyClass {  
   generic <class ItemType>  
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {  
      return ItemType();  
   }  
};  
  
int main() {  
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();  
   GenDelegate<int>^ myDelegate1 =  
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   GenDelegate<double>^ myDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   GenDelegate<int>^ myDelegate =  
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant déclare un délégué générique `GenDelegate<ItemType>`, puis il instancie en l’associant à la méthode `MyMethod` qui utilise le paramètre de type `ItemType`. Deux instances de délégué (entier et double) sont créés et appelés.  
  
```  
// generics_generic_delegate.cpp  
// compile with: /clr  
using namespace System;  
  
// declare generic delegate  
generic <typename ItemType>  
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);  
  
// Declare a generic class:  
generic <typename ItemType>  
ref class MyGenClass {  
public:  
   ItemType MyMethod(ItemType p1, ItemType% p2) {  
      p2 = p1;  
      return p1;  
    }  
};  
  
int main() {  
   int i = 0, j = 0;   
   double m = 0.0, n = 0.0;  
  
   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();  
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();   
  
   // Instantiate a delegate using int.  
   GenDelegate<int>^ MyDelegate1 =   
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   i = MyDelegate1(123, j);  
  
   Console::WriteLine(  
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);  
  
   // Instantiate a delegate using double.  
   GenDelegate<double>^ MyDelegate2 =   
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);  
  
   // Invoke the integer delegate using MyMethod.  
   m = MyDelegate2(0.123, n);  
  
   Console::WriteLine(  
      "Invoking the double delegate: m = {0}, n = {1}", m, n);  
}  
```  
  
```Output  
Invoking the integer delegate: i = 123, j = 123  
Invoking the double delegate: m = 0.123, n = 0.123  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Génériques](../windows/generics-cpp-component-extensions.md)