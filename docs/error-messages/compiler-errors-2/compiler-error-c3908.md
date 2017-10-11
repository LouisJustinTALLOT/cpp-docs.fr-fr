---
title: Erreur du compilateur C3908 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3908
dev_langs:
- C++
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 05b4f772c5c1acf8da9247f27fa92a947a0ffc5b
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3908"></a>Erreur du compilateur C3908
niveau d’accès moins restrictif que celui de 'construction'  
  
 Une méthode d’accesseur de propriété (get ou set) ne peut pas avoir d’accès moins restrictif que l’accès spécifié pour la propriété proprement dite.  De même, pour les méthodes d’accesseur événement.  
  
 Pour plus d’informations, consultez [propriété](../../windows/property-cpp-component-extensions.md) et [événement](../../windows/event-cpp-component-extensions.md).  
  
 L’exemple suivant génère l’erreur C3908 :  
  
```  
// C3908.cpp  
// compile with: /clr  
ref class X {  
protected:  
   property int i {  
   public:   // C3908 property i is protected   
      int get();  
   private:  
      void set(int);   // OK more restrictive  
   };  
};  
```
