---
title: Compilateur avertissement (niveau 4) C4437 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748ba39d9c22a4071307b8df075eab233f3cfbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298325"
---
# <a name="compiler-warning-level-4-c4437"></a>Avertissement du compilateur (niveau 4) C4437
dynamic_cast de la base virtuelle 'classe1' en 'classe2' peut échouer dans certains contextes compilation avec/vd2 ou définissez 'classe2' avec #pragma vtordisp (2) système en vigueur  
  
 Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.  
  
 Le compilateur a rencontré un `dynamic_cast` opération avec les caractéristiques suivantes.  
  
-   La conversion est d’un pointeur de classe de base à un pointeur de la classe dérivée.  
  
-   La classe dérivée hérite pratiquement de la classe de base.  
  
-   La classe dérivée n’a pas un `vtordisp` pour la base virtuelle.  
  
-   La conversion ne se trouve pas dans un constructeur ou un destructeur de la classe dérivée, ou une classe qui concourent hérite de la classe dérivée (Avertissement du compilateur dans le cas contraire, C4436 va être émis).  
  
 L’avertissement indique que le `dynamic_cast` peuvent ne pas fonctionner correctement si elle s’exécute dans un objet partiellement construit.  Cette situation se produit lorsque la fonction englobante est appelée à partir d’un constructeur ou un destructeur d’une classe qui hérite de la classe dérivée qui est nommée dans l’avertissement.  Si la classe dérivée qui est nommée dans l’avertissement n’est jamais plue dérivé, ou la fonction englobante n’est pas appelée au cours de construction d’objet ou une destruction, vous pouvez ignorer l’avertissement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4437 et illustre le problème de génération de code qui découle manquants `vtordisp` champ.  
  
```cpp  
// C4437.cpp  
// To see the warning and runtime assert, compile with: /W4  
// To eliminate the warning and assert, compile with: /W4 /vd2  
//       or compile with: /W4 /DFIX  
#pragma warning(default : 4437)  
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
        func();  
    }  
  
    void func()  
    {  
        A* a = static_cast<A*>(this);  
        B* b = dynamic_cast<B*>(a);     // C4437  
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
 [Avertissement du compilateur (niveau 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)