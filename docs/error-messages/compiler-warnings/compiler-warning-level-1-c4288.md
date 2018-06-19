---
title: Compilateur avertissement (niveau 1) C4288 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4288
dev_langs:
- C++
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c51bdc201b364d76f1692db8ee14973c90923f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276628"
---
# <a name="compiler-warning-level-1-c4288"></a>Avertissement du compilateur (niveau 1) C4288
extension non standard utilisée : 'var' : variable de contrôle de boucle déclarée dans la boucle for est utilisée en dehors de la portée de la boucle ; Il est en conflit avec la déclaration de la portée externe  
  
 Lors de la compilation avec [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et **/Zc:forscope-**, une variable déclarée dans une **pour** boucle a été utilisée après la [pour](../../cpp/for-statement-cpp.md)-portée de la boucle. Une extension Microsoft du langage C++ permet à cette variable de rester dans la portée et C4288 vous rappelle que la première déclaration de la variable n’est pas utilisée.  
  
 Consultez [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) pour plus d’informations sur la spécification de l’extension Microsoft de **pour** boucles avec/Ze.  
  
 L’exemple suivant génère l’erreur C4288 :  
  
```  
// C4288.cpp  
// compile with: /W1 /c /Zc:forScope-  
int main() {  
   int i = 0;    // not used in this program  
   for (int i = 0 ; ; ) ;  
   i++;   // C4288 using for-loop declaration of i  
}  
```