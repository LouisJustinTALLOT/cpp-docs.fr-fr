---
title: Erreur du compilateur C2912 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2912
dev_langs:
- C++
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b165e868f4a2055d692d768c7e5c0164dd34002
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33241221"
---
# <a name="compiler-error-c2912"></a>Erreur du compilateur C2912
la spécialisation explicite 'déclaration' n'est pas une spécialisation d'un modèle de fonction  
  
 Vous ne pouvez pas spécialiser une fonction sans modèle.  
  
 L'exemple suivant génère l'erreur C2912 :  
  
```  
// C2912.cpp  
// compile with: /c  
void f(char);  
template<> void f(char);   // C2912  
template<class T> void f(T);   // OK  
```  
  
 Cette erreur sera également générée suite à la mise en conformité du compilateur dans Visual Studio .NET 2003 : pour chaque spécialisation explicite, vous devez choisir les paramètres de la spécialisation explicite, de sorte qu'ils correspondent aux paramètres du modèle principal.  
  
```  
// C2912b.cpp  
class CF {  
public:  
   template <class A> CF(const A& a) {}   // primary template  
  
   // attempted explicit specialization  
   template <> CF(const char* p) {}   // C2912  
  
   // try the following line instead  
   // template <> CF(const char& p) {}  
};  
```