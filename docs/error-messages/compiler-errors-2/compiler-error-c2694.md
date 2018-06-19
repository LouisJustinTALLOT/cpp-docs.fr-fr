---
title: Erreur du compilateur C2694 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2694
dev_langs:
- C++
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1578b6d7c55272c4b798d0222a1da37f5a749ecc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234119"
---
# <a name="compiler-error-c2694"></a>Erreur du compilateur C2694
'override' : fonction virtuelle de substitution a des spécifications d’exception moins restrictive que la classe de base 'base' de fonction membre virtuel  
  
 Une fonction virtuelle a été substituée, mais sous [/Za](../../build/reference/za-ze-disable-language-extensions.md), la fonction de substitution a moins restrictive [spécification d’exception](../../cpp/exception-specifications-throw-cpp.md).  
  
 L’exemple suivant génère l’erreur C2694 :  
  
```  
// C2694.cpp  
// compile with: /Za /c  
class MyBase {  
public:  
   virtual void f(void) throw(int) {  
   }  
};  
  
class Derived : public MyBase {  
public:  
   void f(void) throw(...) {}   // C2694  
   void f2(void) throw(int) {}   // OK  
};  
```