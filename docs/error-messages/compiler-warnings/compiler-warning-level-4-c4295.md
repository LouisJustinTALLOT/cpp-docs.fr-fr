---
title: Compilateur avertissement (niveau 4) C4295 | Documents Microsoft
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 815a669bc359121b13b1d636009cad81dc332304
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296300"
---
# <a name="compiler-warning-level-4-c4295"></a>Avertissement du compilateur (niveau 4) C4295
  
> '*tableau*' : tableau est trop petit pour comporter un caractère null de fin  
  
Un tableau a été initialisé, mais le dernier caractère dans le tableau n’est pas une valeur null ; accès au tableau sous forme de chaîne peut produire des résultats inattendus.  
  
## <a name="example"></a>Exemple  
  
L’exemple suivant génère l’erreur C4295. Pour résoudre ce problème, vous pouvez déclarer la taille du tableau plus volumineux pour contenir une caractère null de fin de la chaîne de l’initialiseur, ou vous pouvez utiliser une liste d’initialiseurs de tableau pour rendre l’intention clair qu’il s’agit d’un tableau de `char`, pas une chaîne se terminant par null.  
  
```C  
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
