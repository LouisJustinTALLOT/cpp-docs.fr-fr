---
title: Erreur du compilateur C3650 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3650
dev_langs:
- C++
helpviewer_keywords:
- C3650
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a58e0605fcdcb318b3357e142ac2b106bb8c0f7c
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3650"></a>Erreur du compilateur C3650
'méthode_interface' : ne peut pas être utilisé comme substitution explicite, doit être une fonction membre virtuelle de classe de base  
  
 Une tentative a été effectuée pour effectuer une substitution explicite sur un membre qui n’est pas virtuels.  
  
 Pour plus d’informations, consultez [substitutions explicites](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 L’exemple suivant génère l’erreur C3650 :  
  
```  
// C3650.cpp  
// compile with: /clr  
public interface struct I {  
   void a();  
};  
  
public ref class S {  
public:  
   static int f() { return 0; }  
   static int g() { return 0; }  
};  
  
public ref struct T1 : public S, I {  
   virtual int f() new sealed = S::f;   // C3650  
   virtual int g() { return 0; }   // OK does not override S::g  
   virtual void a() new sealed = I::a {}   // OK  
};  
```
