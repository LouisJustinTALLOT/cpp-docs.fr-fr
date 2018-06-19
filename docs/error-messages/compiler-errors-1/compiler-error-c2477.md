---
title: Erreur du compilateur C2477 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2477
dev_langs:
- C++
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca1212a664582f19e91fbf21bde36431ec715946
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33198025"
---
# <a name="compiler-error-c2477"></a>Erreur du compilateur C2477
'membre' : une donnée membre static ne peuvent pas être initialisée via une classe dérivée  
  
 Une donnée membre static de la classe de modèle a été initialisé de manière incorrecte. Il s’agit d’une modification avec rupture avec les versions du compilateur Visual C++ antérieures à Visual Studio .NET 2003, pour se conformer à la norme ISO C++.  
  
 L’exemple suivant génère l’erreur C2477 :  
  
```  
// C2477.cpp  
// compile with: /Za /c  
template <class T>  
struct S {  
   static int n;  
};  
  
struct X {};  
struct A: S<X> {};  
  
int A::n = 0;   // C2477  
  
template<>  
int S<X>::n = 0;  
```