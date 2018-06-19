---
title: Compilateur avertissement (niveau 1) C4377 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef049f85cd17bfeaba243b84da9fca93ae4036b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274779"
---
# <a name="compiler-warning-level-1-c4377"></a>Avertissement du compilateur (niveau 1) C4377
les types natifs sont privés par défaut ; -d1PrivateNativeTypes est déconseillé.  
  
 Dans les versions précédentes, les types natifs dans les assemblys étaient publics par défaut et une option de compilateur interne, non documentée (**/d1PrivateNativeTypes**) a été utilisé pour les rendre privé.  
  
 Tous les types, natifs et CLR, sont désormais privés par défaut dans un assembly, donc **/d1PrivateNativeTypes** n’est plus nécessaire.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4377.  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```