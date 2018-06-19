---
title: Erreur du compilateur C2688 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2688
dev_langs:
- C++
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd2ebb16acfbc5c7d540e877baab909a950c7f55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236012"
---
# <a name="compiler-error-c2688"></a>Erreur du compilateur C2688
'C2::fgrv' : retours covariants avec plusieurs ou l’héritage virtuel non pris en charge pour les fonctions varargs  
  
 Types de retour covariants ne sont pas pris en charge dans Visual C++ lorsqu’une fonction contient des arguments variables.  
  
 Pour résoudre cette erreur, définissez vos fonctions pour qu’ils ne pas utiliser des arguments de variable ou que les valeurs de retour le même pour toutes les fonctions virtuelles.  
  
 L’exemple suivant génère l’erreur C2688 :  
  
```  
// C2688.cpp  
struct G1 {};  
struct G2 {};  
struct G3 : G1, G2 {};  
struct G4 {};  
struct G5 {};  
struct G6 : G4, G5 {};  
struct G7 : G3, G6 {};  
  
struct C1 {  
   virtual G4& fgrv(int,...);  
};  
  
struct C2 : C1 {  
   virtual G7& fgrv(int,...);   // C2688, does not return G4&  
};  
```