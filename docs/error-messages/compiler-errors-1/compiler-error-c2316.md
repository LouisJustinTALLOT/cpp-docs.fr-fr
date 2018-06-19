---
title: Erreur du compilateur C2316 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2316
dev_langs:
- C++
helpviewer_keywords:
- C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 895db6535299a077bc32b6485a360ae450e6c87e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33196842"
---
# <a name="compiler-error-c2316"></a>Erreur du compilateur C2316

> '*exception*' : ne peut pas être intercepté que destructeur et/ou le constructeur de copie est inaccessible  
  
Une exception a été interceptée par valeur ou par référence, mais le constructeur de copie et/ou l’opérateur d’assignation étaient inaccessibles.  
  
Ce code a été accepté par les versions de Visual C++ antérieures à Visual Studio 2003, mais génère maintenant une erreur.  
  
Conformité dans Visual Studio 2015 modifié cette erreur s’appliquent aux instructions catch incorrecte des exceptions MFC dérivées de `CException`. Étant donné que `CException` a un constructeur de copie privé héritée, la classe et ses dérivés sont non reproductible et ne peuvent pas être passés par valeur, ce qui signifie également qu’ils ne peuvent pas être interceptées par valeur. Intercepter les instructions interceptée exceptions MFC par valeur précédemment a conduit à des exceptions non interceptées pendant l’exécution, mais maintenant le compilateur identifie correctement cette situation et le signale une erreur C2316. Pour résoudre ce problème, nous vous recommandons de qu'utiliser les macros MFC TRY/CATCH lieu d’écrivent vos propres gestionnaires d’exceptions, mais qui n’est pas appropriée pour votre code, interceptez les exceptions MFC par référence à la place.   
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2316 :  
  
```  
// C2316.cpp  
// compile with: /EHsc  
#include <stdio.h>  
  
extern "C" int printf_s(const char*, ...);  
  
struct B   
{  
public:  
    B() {}  
    // Delete the following line to resolve.  
private:  
    // copy constructor  
    B(const B&)   
    {  
    }  
};  
  
void f(const B&)   
{  
}  
  
int main()   
{  
    try   
    {  
        B aB;  
        f(aB);  
    }  
    catch (B b) {   // C2316  
        printf_s("Caught an exception!\n");     
    }  
}  
```