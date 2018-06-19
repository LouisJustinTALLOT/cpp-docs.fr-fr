---
title: Compilateur avertissement (niveau 1) C4224 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4224
dev_langs:
- C++
helpviewer_keywords:
- C4224
ms.assetid: 1531cae0-5040-49fd-b149-005bb5085391
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91f74aee988264706d5c74e94c8198a448f66465
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276709"
---
# <a name="compiler-warning-level-1-c4224"></a>Avertissement du compilateur (niveau 1) C4224
extension non standard utilisée : paramètre formel 'identificateur' a été précédemment défini en tant que type  
  
 L’identificateur a été précédemment utilisé comme un `typedef`. Ceci génère un avertissement sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="example"></a>Exemple  
  
```  
// C4224.cpp  
// compile with: /Za /W1 /LD  
typedef int I;  
void func ( int I );  // C4224  
```