---
title: Conversions définies par l’utilisateur (C + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined conversions [C++]
ms.assetid: 8010fd59-2775-4e9a-a6ed-58055032d66f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 721f7135814db0421165fed74e124a7a8fe58e99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170646"
---
# <a name="user-defined-conversions-ccli"></a>Conversions définies par l'utilisateur (C++/CLI)
Cette section décrit les conversions définies par l’utilisateur (UDC) lorsque l’un des types dans la conversion est une référence ou une instance d’un type valeur ou un type référence.  
  
## <a name="implicit-and-explicit-conversions"></a>Conversions implicites et explicites  
 Une conversion définie par l’utilisateur peut être implicite ou explicite.  Une UDC doit être implicite si la conversion n’entraîne pas une perte d’informations. Dans le cas contraire, une UDC explicite doit être définie.  
  
 Constructeur de native d’une classe peut être utilisé pour convertir un type référence ou valeur d’une classe native.  
  
 Pour plus d’informations sur les conversions, consultez [Boxing](../windows/boxing-cpp-component-extensions.md) et [Conversions Standard](../cpp/standard-conversions.md).  
  
```  
// mcpp_User_Defined_Conversions.cpp  
// compile with: /clr  
#include "stdio.h"  
ref class R;  
class N;  
  
value class V {  
   static operator V(R^) {  
      return V();  
   }  
};  
  
ref class R {  
public:  
   static operator N(R^);  
   static operator V(R^) {  
      System::Console::WriteLine("in R::operator N");  
      return V();  
   }  
};  
  
class N {  
public:  
   N(R^) {  
      printf("in N::N\n");  
   }  
};  
  
R::operator N(R^) {  
   System::Console::WriteLine("in R::operator N");  
   return N(nullptr);  
}  
  
int main() {  
   // Direct initialization:  
   R ^r2;  
   N n2(r2);   // direct initialization, calls constructor  
   static_cast<N>(r2);   // also direct initialization  
  
   R ^r3;  
   // ambiguous V::operator V(R^) and R::operator V(R^)  
   // static_cast<V>(r3);     
}  
```  
  
 **Sortie**  
  
```Output  
in N::N  
in N::N  
```  
  
## <a name="convert-from-operators"></a>Opérateurs Convert-From  
 Opérateurs de conversion créer un objet de la classe dans laquelle l’opérateur est défini à partir d’un objet d’une autre classe.  
  
 C++ standard ne prend pas en charge les opérateurs de conversion ; C++ standard utilise les constructeurs à cet effet. Toutefois, lorsque vous utilisez des types CLR, Visual C++ prennent en charge syntaxique pour appeler les opérateurs de conversion.  
  
 Pour interagir correctement avec les autres langages conformes à CLS, vous pouvez souhaiter encapsuler chaque constructeur unaire défini par l’utilisateur pour une classe donnée avec un opérateur de conversion correspondant.  
  
 Opérateurs de conversion :  
  
-   Doit être défini en tant que fonctions statiques.  
  
-   Peut être implicite (pour les conversions qui ne perdent pas la précision, par exemple courte pour int) ou explicite, lorsqu’il y a peut-être une perte de précision.  
  
-   Renvoie un objet de la classe conteneur.  
  
-   Doit avoir le type « de » en tant que le type de paramètre unique.  
  
 L’exemple suivant montre un implicite et explicite » convert-from », l’opérateur de conversion définie par l’utilisateur (UDC).  
  
```  
// clr_udc_convert_from.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
  
   MyDouble(int i) {  
      d = static_cast<double>(i);  
      System::Console::WriteLine("in constructor");  
   }  
  
   // Wrap the constructor with a convert-from operator.  
   // implicit UDC because conversion cannot lose precision  
   static operator MyDouble (int i) {  
      System::Console::WriteLine("in operator");  
      // call the constructor  
      MyDouble d(i);  
      return d;  
   }  
  
   // an explicit user-defined conversion operator  
   static explicit operator signed short int (MyDouble) {  
      return 1;  
   }  
};  
  
int main() {  
   int i = 10;  
   MyDouble md = i;  
   System::Console::WriteLine(md.d);  
  
   // using explicit user-defined conversion operator requires a cast    
   unsigned short int j = static_cast<unsigned short int>(md);  
   System::Console::WriteLine(j);  
}  
```  
  
 **Sortie**  
  
```Output  
in operator  
in constructor  
10  
1  
```  
  
## <a name="convert-to-operators"></a>Opérateurs de conversion  
 Opérateurs Convert pour convertissent un objet de la classe dans laquelle l’opérateur est défini à un autre objet. L’exemple suivant illustre un implicite, convert-, opérateur de conversion définie par l’utilisateur :  
  
```  
// clr_udc_convert_to.cpp  
// compile with: /clr  
using namespace System;  
value struct MyInt {  
   Int32 i;  
  
   // convert MyInt to String^  
   static operator String^ ( MyInt val ) {  
      return val.i.ToString();  
   }  
  
   MyInt(int _i) : i(_i) {}  
};  
  
int main() {  
   MyInt mi(10);  
   String ^s = mi;  
   Console::WriteLine(s);  
}  
```  
  
 **Sortie**  
  
```Output  
10  
```  
  
 Un opérateur de conversion explicite définie par l’utilisateur convert-to est approprié pour les conversions de perdent des données d’une certaine façon. Pour appeler un opérateur de conversion explicite, un cast doit être utilisé.  
  
```  
// clr_udc_convert_to_2.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
   // convert MyDouble to Int32  
   static explicit operator System::Int32 ( MyDouble val ) {  
      return (int)val.d;  
   }  
};  
  
int main() {  
   MyDouble d;  
   d.d = 10.3;  
   System::Console::WriteLine(d.d);  
   int i = 0;  
   i = static_cast<int>(d);  
   System::Console::WriteLine(i);  
}  
```  
  
 **Sortie**  
  
```Output  
10.3  
10  
```  
  
## <a name="to-convert-generic-classes"></a>Pour convertir les classes génériques  
 Vous pouvez convertir une classe générique de T.  
  
```  
// clr_udc_generics.cpp  
// compile with: /clr  
generic<class T>   
public value struct V {  
   T mem;  
   static operator T(V v) {  
      return v.mem;  
   }  
  
   void f(T t) {  
      mem = t;  
   }  
};  
  
int main() {  
   V<int> v;  
   v.f(42);  
   int i = v;  
   i += v;  
   System::Console::WriteLine(i == (42 * 2) );  
}  
```  
  
 **Sortie**  
  
```Output  
True  
```  
  
 Un constructeur de conversion prend un type et l’utilise pour créer un objet.  Un constructeur de conversion est appelé avec une initialisation directe uniquement. les casts n’appellent pas de constructeurs de conversion. Par défaut, les constructeurs de conversion sont explicites pour les types CLR.  
  
```  
// clr_udc_converting_constructors.cpp  
// compile with: /clr  
public ref struct R {  
   int m;  
   char c;  
  
   R(int i) : m(i) { }  
   R(char j) : c(j) { }  
};  
  
public value struct V {  
   R^ ptr;  
   int m;  
  
   V(R^ r) : ptr(r) { }  
   V(int i) : m(i) { }  
};  
  
int main() {   
   R^ r = gcnew R(5);  
  
   System::Console::WriteLine( V(5).m);  
   System::Console::WriteLine( V(r).ptr);  
}  
```  
  
 **Sortie**  
  
```Output  
5  
R  
```  
  
 Dans cet exemple de code, une fonction de conversion statique implicite effectue la même chose qu’un constructeur de conversion explicite.  
  
```  
public value struct V {  
   int m;  
   V(int i) : m(i) {}  
   static operator V(int i) {  
      V v(i*100);  
      return v;  
   }  
};  
  
public ref struct R {  
   int m;  
   R(int i) : m(i) {}  
   static operator R^(int i) {  
      return gcnew R(i*100);  
   }  
};  
  
int main() {  
   V v(13);   // explicit  
   R^ r = gcnew R(12);   // explicit  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
  
   // explicit ctor can't be called here: not ambiguous  
   v = 5;  
   r = 20;  
  
   System::Console::WriteLine(v.m);  
   System::Console::WriteLine(r->m);  
}  
```  
  
 **Sortie**  
  
```Output  
13  
12  
500  
2000  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Classes et structs](../windows/classes-and-structs-cpp-component-extensions.md)