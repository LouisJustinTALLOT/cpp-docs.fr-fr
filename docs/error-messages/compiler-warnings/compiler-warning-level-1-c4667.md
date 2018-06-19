---
title: Compilateur avertissement (niveau 1) C4667 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4667
dev_langs:
- C++
helpviewer_keywords:
- C4667
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af88dc89fce0d95ec252a9cbca4c7a37955244dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280762"
---
# <a name="compiler-warning-level-1-c4667"></a>Avertissement du compilateur (niveau 1) C4667
'fonction' : aucun modèle de fonction défini correspondant de l’instanciation n’imposée  
  
 Vous ne pouvez pas instancier un modèle de fonction qui n’a pas été déclaré.  
  
 L’exemple suivant génère C4667 :  
  
```  
// C4667a.cpp  
// compile with: /LD /W1  
template  
void max(const int &, const int &); // C4667 expected  
```  
  
 Pour éviter cet avertissement, commencez par déclarer le modèle de fonction :  
  
```  
// C4667b.cpp  
// compile with: /LD  
// Declare the function template  
template<typename T>  
const T &max(const T &a, const T &b) {  
   return (a > b) ? a : b;  
}  
// Then forcibly instantiate it with a desired type ... i.e. 'int'  
//  
template  
const int &max(const int &, const int &);  
```