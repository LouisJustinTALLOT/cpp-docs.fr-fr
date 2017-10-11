---
title: Erreur du compilateur C2942 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2942
dev_langs:
- C++
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2685762bc57b4ff0c2d056dff4c246d2286503eb
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2942"></a>Erreur du compilateur C2942
'classe' : type-class-id redéfini comme argument formel d’une fonction  
  
 Vous ne pouvez pas utiliser une classe générique ou de modèle comme argument formel. Vous ne pouvez pas passer un argument directement au constructeur d’une classe générique ou de modèle.  
  
 L’exemple suivant génère l’erreur C2942 :  
  
```  
  
// C2942.cpp  
// compile with: /c  
template<class T>  
struct TC {};   
void f(int TC<int>) {}   // C2942  
  
// OK  
struct TC2 {};  
void f(TC2 i) {}  
```  
  
 L’erreur C2942 peut également se produire lors de l’utilisation de génériques :  
  
```  
// C2942b.cpp  
// compile with: /clr /c  
generic<class T>  
ref struct GC {};  
void f(int GC<int>) {}   // C2942  
ref struct GC2 { };  
void f(int GC2) {}  
```
