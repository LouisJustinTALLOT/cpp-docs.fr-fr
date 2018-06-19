---
title: Compilateur avertissement (niveau 1) C4436 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1da06a329a9c0bdfcff6877ce69c8e3672619bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281640"
---
# <a name="compiler-warning-level-1-c4436"></a>Avertissement du compilateur (niveau 1) C4436
dynamic_cast de la base virtuelle 'classe1' en 'classe2' dans le constructeur ou un destructeur peut échouer avec un objet partiellement construit compilation avec/vd2 ou définir 'classe2' avec #pragma vtordisp (2) système en vigueur  
  
 Le compilateur a rencontré un `dynamic_cast` opération avec les caractéristiques suivantes.  
  
-   La conversion est d’un pointeur de classe de base à un pointeur de la classe dérivée.  
  
-   La classe dérivée hérite pratiquement de la classe de base.  
  
-   La classe dérivée n’a pas un `vtordisp` pour la base virtuelle.  
  
-   Le cast se trouvent dans un constructeur ou un destructeur de la classe dérivée, ou une classe qui concourent hérite de la classe dérivée.  
  
 L’avertissement indique la `dynamic_cast` peuvent ne pas fonctionner correctement, si elle s’exécute dans un objet partiellement construit.  Cela se produit si le constructeur/destructeur dérivé est d’utiliser un sous-objet d’un objet dérivé ultérieure.  Si la classe dérivée est nommée dans l’avertissement n’est jamais plue dérivé, l’avertissement peut être ignoré.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4436 et illustre le problème de génération de code qui découle manquants `vtordisp` champ.  
  
```cpp  
// C4436.cpp  
// To see the warning and runtime assert, compile with: /W1  
// To eliminate the warning and assert, compile with: /W1 /vd2  
//       or compile with: /W1 /DFIX  
#include <cassert>  
  
struct A  
{  
public:  
    virtual ~A() {}  
};  
  
#if defined(FIX)  
#pragma vtordisp(push, 2)  
#endif  
struct B : virtual A  
{  
    B()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4436  
        assert(this == b);              // assert unless compiled with /vd2  
    }  
};  
#if defined(FIX)  
#pragma vtordisp(pop)  
#endif  
  
struct C : B  
{  
    int i;  
};  
  
int main()  
{  
    C c;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [dynamic_cast, opérateur](../../cpp/dynamic-cast-operator.md)   
 [vtordisp](../../preprocessor/vtordisp.md)   
 [Avertissement du compilateur (niveau 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)