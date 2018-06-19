---
title: Erreur du compilateur C2001 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f56eabbcb5ca322d7549c21a56893a8e13d9261
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164828"
---
# <a name="compiler-error-c2001"></a>Erreur du compilateur C2001
saut de ligne dans la constante  
  
 Une constante de chaîne ne peut pas se poursuivre sur une deuxième ligne, sauf si vous procédez comme suit :  
  
-   La première ligne d’une barre oblique de fin.  
  
-   Fermez la chaîne sur la première ligne par un guillemet double et ouvrez la chaîne sur la ligne suivante avec un autre guillemet double.  
  
 Fin de la première ligne \n n’est pas suffisant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2001 :  
  
```  
// C2001.cpp  
// C2001 expected  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,  
             world");  
    printf_s("Hello,\n  
             world");  
}  
```  
  
## <a name="example"></a>Exemple  
 Les espaces au début de la ligne suivante après un caractère de continuation de ligne sont inclus dans la constante de chaîne. Aucun des exemples ci-dessus incorporer un caractère de saut de ligne dans la constante de chaîne. Vous pouvez incorporer un caractère de saut de ligne comme indiqué ici :  
  
```  
// C2001b.cpp  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,\n\  
             world");  
  
    printf_s("Hello,\  
             \nworld");  
  
    printf_s("Hello,\n"  
             "world");  
  
    printf_s("Hello,"  
             "\nworld");  
  
    printf_s("Hello,"  
             " world");  
  
    printf_s("Hello,\  
             world");  
}  
```