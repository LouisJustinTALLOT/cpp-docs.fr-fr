---
title: Erreur du compilateur C2657 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2657
dev_langs:
- C++
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 70814ce7423bee3147f68d6298babc10eeac56fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231370"
---
# <a name="compiler-error-c2657"></a>Erreur du compilateur C2657
' classe :: *' trouvé au début d’une instruction (vous avez oublié de spécifier un type ?)  
  
 Début de la ligne avec un identificateur de pointeur vers membre.  
  
 Cette erreur peut résulter d’un spécificateur de type manquant dans la déclaration d’un pointeur vers un membre.  
  
 L’exemple suivant génère l’erreur C2657 :  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```