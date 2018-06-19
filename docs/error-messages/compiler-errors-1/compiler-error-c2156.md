---
title: Erreur du compilateur C2156 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2156
dev_langs:
- C++
helpviewer_keywords:
- C2156
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 288757f93e0cf7c478fae739f106482b5ba8a016
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167305"
---
# <a name="compiler-error-c2156"></a>Erreur du compilateur C2156
pragma doit être à l'extérieur de la fonction  
  
 Un pragma qui doit être spécifié à un niveau global (en dehors d’un corps de fonction) se trouve dans une fonction.  
  
 L’exemple suivant génère l’erreur C2156 :  
  
```  
// C2156.cpp  
#pragma optimize( "l", on )   // OK  
int main() {  
   #pragma optimize( "l", on )   // C2156  
}  
```