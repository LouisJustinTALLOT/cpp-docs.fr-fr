---
title: Erreur du compilateur C2464 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98949ba463f432666753cb39de37bb4bf8f7276f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226024"
---
# <a name="compiler-error-c2464"></a>Erreur du compilateur C2464
'identificateur' : Impossible d’utiliser 'new' pour allouer une référence  
  
 Un identificateur de référence a été alloué avec la `new` opérateur. Références ne sont pas des objets de mémoire, par conséquent, `new` ne peut pas retourner un pointeur à ceux-ci. Utilisez la syntaxe de déclaration de variable standard pour déclarer une référence.  
  
 L’exemple suivant génère l’erreur C2464 :  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```