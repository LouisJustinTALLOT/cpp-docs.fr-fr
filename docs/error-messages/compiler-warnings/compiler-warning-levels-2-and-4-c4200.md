---
title: Compilateur avertissement (niveaux 2 et 4) C4200 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4200
dev_langs:
- C++
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ffc789c3c4da5caf50f0657e17ddabe40a5773c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294948"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>Avertissement du compilateur (niveaux 2 et 4) C4200
extension non standard utilisée : tableau de taille zéro dans un struct/union  
  
 Indique qu'une structure ou une union contient un tableau de taille zéro.  
  
 La déclaration d'un tableau de taille zéro est une extension Microsoft. Cela provoque un avertissement de niveau 2 lors de la compilation d'un fichier C++ et un avertissement de niveau 4 lors de la compilation d'un fichier C. La compilation C++ génère aussi cet avertissement : « Impossible de générer un constructeur de copie ou un opérateur d'assignation de copie lorsque UDT contient un tableau de taille zéro. » Cet exemple génère l'avertissement C4200 :  
  
```cpp  
// C4200.cpp  
// compile by using: cl /W4 c4200.cpp  
struct A {  
    int a[0];  // C4200  
};  
int main() {  
}  
```  
  
 Cette extension non standard est souvent utilisée pour assurer une interface entre le code et les structures de données externes qui ont une longueur variable. Si ce scénario s'applique à votre code, vous pouvez désactiver l'avertissement :  
  
## <a name="example"></a>Exemple  
  
```cpp  
// C4200b.cpp  
// compile by using: cl /W4 c4200a.cpp  
#pragma warning(disable : 4200)  
struct A {  
    int a[0];  
};  
int main() {  
}  
```