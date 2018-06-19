---
title: Compilateur avertissement (niveau 1) C4812 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4812
dev_langs:
- C++
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 05ff26f9adf9548553cd76033bba3aa9cefe9417
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282793"
---
# <a name="compiler-warning-level-1-c4812"></a>Avertissement du compilateur (niveau 1) C4812
style de déclaration obsolète : utilisez 'nouvelle_syntaxe' à la place  
  
 Dans la version actuelle de Visual C++, la spécialisation du constructeur explicite est toujours prise en charge, mais elle ne le sera peut être plus dans les versions ultérieures.  
  
 L’exemple suivant génère l’erreur C4812 :  
  
```  
// C4812.cpp  
// compile with: /W1 /c  
template <class T>   
class MyClass;  
  
template<class T>  
class MyClass<T*> {  
   MyClass();  
};  
  
template<class T>  
MyClass<T*>::MyClass<T*>() {}   // C4812  
// try the following line instead  
// MyClass<T*>::MyClass() {}  
```