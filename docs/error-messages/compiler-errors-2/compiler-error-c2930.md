---
title: Erreur du compilateur C2930 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2930
dev_langs:
- C++
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2d1890b86292cec062d64e1fe56c5769178444
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2930"></a>Erreur du compilateur C2930
'class' : type-class-id redéfini comme énumérateur de 'enum identifier'  
  
 Vous ne pouvez pas utiliser une classe générique ni de modèle en tant que membre d’une énumération.  
  
 Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.  
  
 L’exemple suivant génère l’erreur C2930 :  
  
```  
// C2930.cpp  
// compile with: /c  
template<class T>   
class x{};  
enum SomeEnum { x };   // C2930  
  
class y{};  
enum SomeEnum { y };  
```  
  
 L’erreur C2930 peut également se produire lors de l’utilisation de génériques :  
  
```  
// C2930c.cpp  
// compile with: /clr /c  
generic<class T>   
ref struct GC {};  
enum SomeEnum { GC };   // C2930  
  
ref struct GC2 {};  
enum SomeEnum2 { GC2 };  
```