---
title: Du compilateur (niveau 1) d’avertissement C4190 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e62f6bcfaa499338d5fde1d09cb91574241ce8a0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277892"
---
# <a name="compiler-warning-level-1-c4190"></a>Du compilateur (niveau 1) d’avertissement C4190
'identificateur1' a une liaison C spécifiée, mais retourne UDT 'identificateur2' qui est incompatible avec C  
  
 Une fonction ou un pointeur vers une fonction a un type UDT (user defined type, classe, structure, enum ou union) en tant que type de retour et `extern` une liaison de « C ». Cela est légal si :  
  
-   Tous les appels à cette fonction se produisent à partir de C++.  
  
-   La définition de la fonction est en C++.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```