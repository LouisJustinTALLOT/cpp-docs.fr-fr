---
title: Compilateur avertissement (niveau 1) C4075 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4075
dev_langs:
- C++
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9a0d9fb3808af9ed05454b5b07d471303abc654
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282881"
---
# <a name="compiler-warning-level-1-c4075"></a>Avertissement du compilateur (niveau 1) C4075
initialiseurs placés dans une zone d'initialisation non reconnue  
  
 Un [#pragma init_seg](../../preprocessor/init-seg.md) utilise un nom de section non reconnu. Le compilateur ignore la commande **pragma** .  
  
 L’exemple suivant génère l’avertissement C4075 :  
  
```  
// C4075.cpp  
// compile with: /W1  
#pragma init_seg("mysegg")   // C4075  
  
// try..  
// #pragma init_seg(user)  
  
int main() {  
}  
```