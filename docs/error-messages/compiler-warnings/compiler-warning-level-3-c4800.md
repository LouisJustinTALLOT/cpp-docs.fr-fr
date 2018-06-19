---
title: Avertissement (niveau 3) du compilateur C4800 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed4b14ae2f3af3218909d6cd4609f1f45d3d7cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293632"
---
# <a name="compiler-warning-level-3-c4800"></a>Avertissement du compilateur (niveau 3) C4800  
  
> '*type*' : valeur forcée à booléenne 'true' ou 'false' (avertissement sur les performances)  
  
Cet avertissement est généré lorsqu’une valeur qui n’est pas `bool` est assignée ou forcée dans le type `bool`. En règle générale, ce message est provoqué par l’assignation `int` variables à `bool` variables où le `int` variable contient des valeurs **true** et **false**et ne peut être redéclaration comme type `bool`. Si vous ne pouvez pas réécrire l’expression pour utiliser le type `bool`, vous pouvez alors ajouter «`!=0`» à l’expression, ce qui donne le type d’expression `bool`. Effectuer un cast de l’expression en type `bool` ne désactive pas l’avertissement qui est lié à la conception.  
  
Cet avertissement n’est plus généré dans Visual Studio 2017.  
  
## <a name="example"></a>Exemple
  
 L’exemple suivant génère l’erreur C4800 et montre comment la corriger :  
  
```cpp  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // To fix, instead try:  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```