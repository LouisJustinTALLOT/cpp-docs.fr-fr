---
title: Erreur du compilateur C3722 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3722
dev_langs:
- C++
helpviewer_keywords:
- C3722
ms.assetid: 3cb28363-5eff-4548-bd0d-d5c615846353
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5948e0f295b9a086427c30617be055205bf8ab83
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3722"></a>Erreur du compilateur C3722
un événement générique n’est pas autorisé.  
  
 Le compilateur autorise uniquement des fonctions, des structs et classes génériques.  Pour plus d’informations, consultez [Génériques](../../windows/generics-cpp-component-extensions.md).  
  
 L’exemple suivant génère l’erreur C3722 :  
  
```  
// C3722.cpp  
// compile with: /clr  
generic <typename T>  
public delegate void MyEventHandler(System::Object^ sender, System::EventArgs^ e, T optional);  
  
generic <class T>  
public ref struct MyButton {  
   generic<typename U>  
   event MyEventHandler<U>^ Click;   // C3722  
};  
```
