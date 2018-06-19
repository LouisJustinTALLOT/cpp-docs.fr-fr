---
title: Compilateur avertissement (niveau 1) C4086 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4086
dev_langs:
- C++
helpviewer_keywords:
- C4086
ms.assetid: 9248831b-22bf-47af-8684-bfadb17e94fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 541543cde39821a938290d1a8f5ce2063c8fc997
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275208"
---
# <a name="compiler-warning-level-1-c4086"></a>Avertissement du compilateur (niveau 1) C4086
le paramètre pragma attendu doit être '1', '2', '4', '8', ou '16'  
  
 Le paramètre pragma n’a pas la valeur requise (1, 2, 4, 8 ou 16).  
  
## <a name="example"></a>Exemple  
  
```  
// C4086.cpp  
// compile with: /W1 /LD  
#pragma pack( 3 ) // C4086  
```