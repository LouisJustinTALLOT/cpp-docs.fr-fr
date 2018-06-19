---
title: Erreur du compilateur C2191 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2191
dev_langs:
- C++
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aa4b590b494355450909032c78822553004beddc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169434"
---
# <a name="compiler-error-c2191"></a>Erreur du compilateur C2191
seconde liste de paramètres plus longue que la première  
  
 Une fonction C a été déclarée une seconde fois avec une liste de paramètres plus longue. C ne prend pas en charge les fonctions surchargées.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2191 :  
  
```  
// C2191.c  
// compile with: /Za /c  
void func( int );  
void func( int, float );   // C2191 different parameter list  
void func2( int, float );   // OK  
```