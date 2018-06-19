---
title: Avertissement (niveau 1) du compilateur C4297 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2c37f82b646902d08c8fc2ce633948969d0755f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281974"
---
# <a name="compiler-warning-level-1-c4297"></a>Avertissement du compilateur (niveau 1) C4297
'fonction' : la fonction lève une exception alors qu'elle est présumée ne pas le faire  
  
 Une déclaration de fonction contient un (l’éventuellement implicite) `noexcept` spécificateur, vide `throw` spécificateur d’exception, ou un [__declspec (nothrow)](../../cpp/nothrow-cpp.md) attribut et la définition contient un ou plusieurs [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) instructions. Pour résoudre l'avertissement C4297, ne tentez pas de lever des exceptions dans les fonctions qui sont déclarées `__declspec(nothrow)`, `noexcept(true)` ou `throw()`. Vous pouvez également supprimer la spécification `noexcept`, `throw()` ou `__declspec(nothrow)`.  
  
 Par défaut, le compilateur génère des spécificateurs `noexcept(true)` implicites pour les fonctions annulatrices d'allocation et les destructeurs définis par l'utilisateur, ainsi que pour les fonctions membres spéciales générées par le compilateur. Cela est conforme à la norme ISO C++11. Pour empêcher la génération des spécificateurs de noexcept implicites et rétablir le comportement non standard de Visual Studio 2013, utilisez le **/Zc:implicitNoexcept-** option du compilateur. Pour plus d’informations, consultez [/Zc : implicitnoexcept (spécificateurs d’exceptions implicites)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).  
  
 Pour plus d’informations sur les spécifications d’exceptions, consultez [spécifications d’Exception (throw)](../../cpp/exception-specifications-throw-cpp.md). Consultez également [/EH (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) pour plus d’informations sur la façon de modifier le comportement des exceptions au moment de la compilation.  
  
 Cet avertissement est également généré pour __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) fonctions marquées extern « C », même s’ils sont des fonctions C++.  
  
 L'exemple suivant génère l'avertissement C4297 :  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```