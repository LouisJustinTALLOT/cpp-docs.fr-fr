---
title: Erreur du compilateur C2588 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67eb6362ff55e09b05349d10fcdc2377d8ff2996
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231668"
---
# <a name="compiler-error-c2588"></a>Erreur du compilateur C2588
' :: ~ identificateur ' : destructeur global non conforme  
  
 Le destructeur est défini pour un élément autre qu’une classe, structure ou union. Cette opération n’est pas autorisée.  
  
 Cette erreur peut être provoquée par un manquant nom de classe, structure ou union sur le côté gauche de la résolution de portée (`::`) (opérateur).  
  
 L’exemple suivant génère l’erreur C2588 :  
  
```  
// C2588.cpp  
~F();   // C2588  
```