---
title: "R&#233;solution du nom pour les types d&#233;pendants | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 34066bb4-0c79-4fd8-bda7-539a60a277ab
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# R&#233;solution du nom pour les types d&#233;pendants
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilisez **typename** pour les noms qualifiés dans les définitions de modèle pour indiquer au compilateur que le nom qualifié donné identifie un type.  Pour plus d'informations, consultez [typename](../cpp/typename.md).  
  
```cpp  
// template_name_resolution1.cpp  
#include <stdio.h>  
template <class T> class X  
{  
public:  
   void f(typename T::myType* mt) {}  
};  
  
class Yarg  
{  
public:  
   struct myType { };  
};  
  
int main()  
{  
   X<Yarg> x;  
   x.f(new Yarg::myType());  
   printf("Name resolved by using typename keyword.");  
}  
```  
  
### Sortie  
  
```  
Name resolved by using typename keyword.  
```  
  
 La recherche de noms dépendants examine les noms dans le contexte de la définition de modèle, \(dans l'exemple suivant ce contexte trouverait `myFunction(char)`\) et le contexte de l'instanciation de modèle.  Dans l'exemple suivant, le modèle est instancié dans main. Par conséquent, `MyNamespace::myFunction` est visible à partir du point d'instanciation et est choisi comme la meilleure correspondance.  Si `MyNamespace::myFunction` était renommé, `myFunction(char)` serait appelé à la place.  
  
 Tous les noms sont résolus comme s'ils étaient des noms dépendants.  Néanmoins, nous vous recommandons d'utiliser des noms complets en cas de conflit éventuel.  
  
```cpp  
//template_name_resolution2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
void myFunction(char)  
{  
   cout << "Char myFunction" << endl;  
}  
  
template <class T> class Class1  
{  
public:  
   Class1(T i)  
   {  
      // If replaced with myFunction(1), myFunction(char)  
      // will be called  
      myFunction(i);  
}  
};  
  
namespace MyNamespace  
{  
   void myFunction(int)  
   {  
      cout << "Int MyNamespace::myFunction" << endl;  
   }  
};  
  
using namespace MyNamespace;  
  
int main()  
{  
   Class1<int>* c1 = new Class1<int>(100);  
}  
```  
  
### Sortie  
  
```  
Int MyNamespace::myFunction  
```  
  
### Levée des ambiguïtés de modèle  
 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] applique les règles standard C\+\+98\/03\/11 pour éviter les ambiguïtés avec le mot clé template.  Dans l'exemple suivant, [!INCLUDE[cpp_dev10_long](../build/includes/cpp_dev10_long_md.md)] accepterait les lignes non conformes et les lignes conformes. [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] n'accepte que les lignes conformes.  
  
```cpp  
#include <iostream>  
#include <ostream>  
#include <typeinfo>  
using namespace std;  
  
template <typename T> struct Allocator {  
    template <typename U> struct Rebind {  
        typedef Allocator<U> Other;  
    };  
};  
  
template <typename X, typename AY> struct Container {  
    #if defined(NONCONFORMANT)  
        typedef typename AY::Rebind<X>::Other AX; // nonconformant  
    #elif defined(CONFORMANT)  
        typedef typename AY::template Rebind<X>::Other AX; // conformant  
    #else  
        #error Define NONCONFORMANT or CONFORMANT.  
    #endif  
};  
  
int main() {  
    cout << typeid(Container<int, Allocator<float>>::AX).name() << endl;  
}  
```  
  
 La conformité avec les règles de levée des ambiguïtés est requise car, par défaut, C\+\+ suppose que `AY::Rebind` n'est pas un modèle. Par conséquent, le compilateur interprète le `<` suivant comme un signe Inférieur à.  Il doit savoir si `Rebind` est un modèle afin de pouvoir analyser correctement `<` comme crochet angulaire.  
  
## Voir aussi  
 [Résolution de noms](../cpp/templates-and-name-resolution.md)