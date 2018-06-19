---
title: Erreur du compilateur C2735 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2735
dev_langs:
- C++
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab970aa4e46ed0206f311e100f7ee777907aff8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33232667"
---
# <a name="compiler-error-c2735"></a>Erreur du compilateur C2735
' mot_clé ' n’est pas autorisé dans le spécificateur de type de paramètre formel  
  
 Le mot clé n’est pas valide dans ce contexte.  
  
 L’exemple suivant génère l’erreur C2735 :  
  
```  
// C2735.cpp  
void f(inline int){}   // C2735  
```