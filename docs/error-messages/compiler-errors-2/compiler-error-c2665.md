---
title: Erreur du compilateur C2665 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18cc99d6ea0a45e7c096a13cfe57dc841ca351bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235778"
---
# <a name="compiler-error-c2665"></a>Erreur du compilateur C2665
'fonction' : aucune des surcharges nombre1 peut convertir le paramètre nombre2 à partir du type 'type'  
  
 Un paramètre de la fonction surchargée ne peut pas être converti au type requis.  Solutions possibles :  
  
-   Fournissez un opérateur de conversion.  
  
-   Utilisez une conversion explicite.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2665.  
  
```  
// C2665.cpp  
void func(short, char*){}  
void func(char*, char*){}  
  
int main() {  
   func(0, 1);   // C2665  
   func((short)0, (char*)1);   // OK  
}  
```