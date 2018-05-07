---
title: Erreur du compilateur C2712 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2712
dev_langs:
- C++
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c26c5d7a24c022cacf4c20687b2d8c58f7e9e342
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2712"></a>Erreur du compilateur C2712
impossible d'utiliser __try dans les fonctions nécessitant un déroulement d'objet  
  
 Erreur C2712 peut se produire si vous utilisez [/EHsc](../../build/reference/eh-exception-handling-model.md), et une fonction avec la gestion structurée des exceptions également possède des objets nécessitant un déroulement (destruction).  
  
 Solutions possibles :  
  
-   Déplacez le code nécessitant la gestion structurée des exceptions vers une autre fonction.  
  
-   Réécrivez les fonctions qui utilisent la gestion structurée des exceptions pour éviter l'utilisation de variables locales et de paramètres possédant des destructeurs. N'utilisez pas la gestion structurée des exceptions dans les constructeurs ni les destructeurs.  
  
-   Compilez sans /EHsc.  
  
 Erreur C2712 peut également se produire si vous appelez une méthode déclarée à l’aide de la [__event](../../cpp/event.md) (mot clé). Étant donné que l’événement peut être utilisé dans un environnement multithread, le compilateur génère du code qui empêche toute manipulation de l’objet événement sous-jacent, puis joint le code généré dans une gestion structurée des exceptions [try-finally, instruction](../../cpp/try-finally-statement.md). Par conséquent, l’erreur C2712 se produit si vous appelez la méthode d’événement et passez par valeur un argument dont le type possède un destructeur. Dans ce cas, une solution consiste à passer l’argument en tant que référence constante.  
  
## <a name="example"></a>Exemple  
 L’erreur C2712 peut également se produire si vous compilez avec **/CLR : pure** et déclarer un tableau statique de pointeurs vers des fonctions dans un `__try` bloc. Un membre statique exige du compilateur utilise l’initialisation dynamique sous **/CLR : pure**, ce qui implique la gestion des exceptions C++. Toutefois, la gestion des exceptions C++ n'est pas autorisée dans un bloc `__try`.  
  
 Les options de compilateur **/clr:pure** et **/clr:safe** sont dépréciées dans Visual Studio 2015.  
  
 L'exemple suivant génère l'erreur C2712 et montre comment la corriger.  
  
```  
// C2712.cpp  
// compile with: /clr:pure /c  
struct S1 {  
   static int smf();  
   void fnc();  
};  
  
void S1::fnc() {  
   __try {  
      static int (*array_1[])() = {smf,};   // C2712  
  
      // OK  
      static int (*array_2[2])();  
      array_2[0] = smf;  
    }  
    __except(0) {}  
}  
```