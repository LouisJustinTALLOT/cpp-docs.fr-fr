---
title: Erreur du compilateur C2942 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2942
dev_langs:
- C++
helpviewer_keywords:
- C2942
ms.assetid: 13abf744-8fa1-450d-886d-e5717c04956e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55dc1fc5c2762751762b3798d28245224281ce67
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33245046"
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