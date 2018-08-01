---
title: Comportement non standard | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1369614cfd20d39fee3f2c2dd1ca7436ae742d2b
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405377"
---
# <a name="nonstandard-behavior"></a>Comportement non standard
Les sections suivantes répertorient certaines des situations dans lesquelles l'implémentation Visual C++ n'est pas conforme à la norme C++. Les numéros de section ci-dessous correspondent aux numéros de section de la norme C++11 (ISO/IEC 14882:2011(E)).  
  
 La liste des limites du compilateur qui diffèrent de celles définies dans la norme C++ est indiquée dans [limites du compilateur](../cpp/compiler-limits.md).  
  
## <a name="covariant-return-types"></a>Types de retour covariant  
 Les classes de base virtuelle ne sont pas prises en charge en tant que types de retour covariants lorsque la fonction virtuelle a un nombre d'arguments variable. Ceci n'est pas conforme à la section 10.3, paragraphe 7 de la spécification ISO C++. L’exemple suivant n’est pas compilé, ce qui donne d’erreur du compilateur [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)  
  
```cpp  
// CovariantReturn.cpp  
class A   
{  
   virtual A* f(int c, ...);   // remove ...  
};  
  
class B : virtual A  
{  
   B* f(int c, ...);   // C2688 remove ...  
};  
```  
  
## <a name="binding-nondependent-names-in-templates"></a>Liaison de noms non dépendants dans des modèles  
 Le compilateur Visual C++ ne prend pas en charge actuellement la liaison des noms non dépendants lors de l'analyse initiale d'un modèle. Ceci n'est pas conforme à la section 14.6.3 de la spécification ISO C++. Cela peut provoquer la déclaration de surcharges après le modèle à afficher (mais avant que le modèle soit instancié).  
  
```cpp  
#include <iostream>  
using namespace std;  
  
namespace N {  
   void f(int) { cout << "f(int)" << endl;}  
}  
  
template <class T> void g(T) {  
    N::f('a');   // calls f(char), should call f(int)  
}  
  
namespace N {  
    void f(char) { cout << "f(char)" << endl;}  
}  
  
int main() {  
    g('c');  
}  
// Output: f(char)  
```  
  
## <a name="function-exception-specifiers"></a>Spécificateurs d'exceptions de fonctions  
 Les spécificateurs d'exceptions de fonction autres que `throw()` sont analysés, mais pas utilisés. Ceci n'est pas conforme à la section 15.4 de la spécification ISO C++. Exemple :  
  
```cpp  
void f() throw(int); // parsed but not used  
void g() throw();    // parsed and used  
```  
  
 Pour plus d’informations sur les spécifications d’exceptions, consultez [les spécifications d’exceptions](../cpp/exception-specifications-throw-cpp.md).  
  
## <a name="chartraitseof"></a>char_traits::eof()  
 La norme C++ stipule que [char_traits::eof](../standard-library/char-traits-struct.md#eof) ne doit pas correspondre à un valide `char_type` valeur. Le compilateur Visual C++ applique cette contrainte de type **char**, mais pas pour le type **wchar_t**. Ceci n’est pas conforme à l’exigence du tableau 62 de la section 12.1.1 de la spécification ISO C++. C'est ce qu'illustre l'exemple ci-dessous.  
  
```cpp  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    char_traits<char>::int_type int2 = char_traits<char>::eof();  
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;  
  
    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();  
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;  
}  
```  
  
## <a name="storage-location-of-objects"></a>Emplacement de stockage des objets  
 La norme C++ (section 1.8, paragraphe 6) exige que les objets C++ complets aient des emplacements de stockage uniques. Toutefois, avec Visual C++, il existe certaines situations dans lesquelles des types sans données membres partagent un emplacement de stockage avec d'autres types pendant la durée de vie de l'objet.