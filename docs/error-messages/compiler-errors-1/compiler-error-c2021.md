---
title: Erreur du compilateur C2021 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2021
dev_langs:
- C++
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae1c3640b4fbe5b1473c2e678406321f5533e586
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167500"
---
# <a name="compiler-error-c2021"></a>Erreur du compilateur C2021
valeur d’exposant attendue, non 'caractère'  
  
 Le caractère utilisé comme exposant d’une constante à virgule flottante n’est pas un nombre valid. Veillez à utiliser un exposant dans la plage.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2021 :  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## <a name="example"></a>Exemple  
 Solution possible :  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```