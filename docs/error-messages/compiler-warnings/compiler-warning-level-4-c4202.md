---
title: Compilateur avertissement (niveau 4) C4202 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4202
dev_langs:
- C++
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dea55835c75a0ac1d5646a542675eefa2c5e5254
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293008"
---
# <a name="compiler-warning-level-4-c4202"></a>Avertissement du compilateur (niveau 4) C4202
extension non standard utilisée : '...' : paramètre de prototype non conforme de liste de nom dans  
  
 Une définition de fonction de style ancien contient des arguments variables. Ces définitions génèrent une erreur sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="example"></a>Exemple  
  
```  
// C4202.c  
// compile with: /W4  
void func( a, b, ...)   // C4202  
int a, b;  
{}  
  
int main()  
{  
}  
```