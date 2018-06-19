---
title: Erreur du compilateur C2781 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2781
dev_langs:
- C++
helpviewer_keywords:
- C2781
ms.assetid: f29b9963-f55b-427c-8db6-50f37713df5a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa42627085494047e10644f86a938b9311cb1625
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235519"
---
# <a name="compiler-error-c2781"></a>Erreur du compilateur C2781
'déclaration' : attend au moins value1 argument - valeur2 fournis  
  
 Un modèle de fonction avec une liste de paramètres de variable a trop peu d’arguments.  
  
 L’exemple suivant génère l’erreur C2781 :  
  
```  
// C2781.cpp  
template<typename T>  
void f(T, T, ...){}  
  
int main() {  
   f(1);   // C2781  
  
   // try the following line instead  
   f(1,1);  
}  
```