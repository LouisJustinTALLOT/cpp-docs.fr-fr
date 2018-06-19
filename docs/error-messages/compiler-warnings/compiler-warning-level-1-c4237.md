---
title: Compilateur avertissement (niveau 1) C4237 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4237
dev_langs:
- C++
helpviewer_keywords:
- C4237
ms.assetid: f2e86c4b-80d8-460e-9429-83c5f3f5d7ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3dfefb2dc7dd04f2334b2b7d222153d5ee351ae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277577"
---
# <a name="compiler-warning-level-1-c4237"></a>Avertissement du compilateur (niveau 1) C4237
' mot_clé ' n’est pas encore pris en charge, mais réservé pour un usage ultérieur  
  
 Un mot clé dans la spécification C++ n’est pas implémenté dans le compilateur Visual C++, mais le mot clé n’est pas disponible comme symbole défini par l’utilisateur.  
  
 L’exemple suivant génère l’erreur C4237 :  
  
```  
// C4237.cpp  
// compile with: /W1 /c  
int export;   // C4237  
```