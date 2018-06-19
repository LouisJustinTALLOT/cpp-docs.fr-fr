---
title: Erreur du compilateur C3452 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3452
dev_langs:
- C++
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: baa8470d6c7c0ffe38c6f6be07bb67a9ae932de9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249628"
---
# <a name="compiler-error-c3452"></a>Erreur du compilateur C3452
le membre argument de la liste n'est pas une constante  
  
 Un argument a été passé à un attribut qui attendait une constante, valeur qui peut être évaluée au moment de la compilation.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3452.  
  
```  
// C3452.cpp  
// compile with: /c  
int i;  
[module( name="mod", type=dll, custom={i} ) ];   // C3452  
// try the following line instead  
// [module( name="mod", type=dll, custom={"a"} ) ];  
```