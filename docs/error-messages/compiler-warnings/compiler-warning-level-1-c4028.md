---
title: Compilateur avertissement (niveau 1) C4028 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4028
dev_langs:
- C++
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c96abd732a00e5b37b48be8c3053cbfbb8c37c37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274357"
---
# <a name="compiler-warning-level-1-c4028"></a>Compilateur avertissement (niveau 1) C4028
paramètre formel 'nombre' différent de la déclaration  
  
 Le type du paramètre formel ne correspond pas avec le paramètre correspondant dans la déclaration. Le type dans la déclaration d’origine est utilisé.  
  
 Cet avertissement est uniquement valide pour le code source C.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4028.  
  
```  
// C4028.c  
// compile with: /W1 /Za  
void f(int , ...);  
void f(int i, int j) {}   // C4028  
  
void g(int , int);  
void g(int i, int j) {}   // OK  
  
int main() {}  
```