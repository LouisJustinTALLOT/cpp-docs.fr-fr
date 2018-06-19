---
title: Erreur du compilateur C2917 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2917
dev_langs:
- C++
helpviewer_keywords:
- C2917
ms.assetid: ec9da9ee-0f37-47b3-87dd-19ef5a14dc4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecc5f8634505dc8b63cb4cbdbbb9aa31973e7475
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254548"
---
# <a name="compiler-error-c2917"></a>Erreur du compilateur C2917
'name' : paramètre de modèle non valide  
  
 Une liste de paramètres de modèles contient un identificateur qui n’était pas un paramètre de modèle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2917.  
  
```  
// C2917.cpp  
// compile with: /c  
template<class T> class Vector {  
   void sort();  
};  
  
template<class T*> void Vector<T>::sort() {}   // C2917  
// try the following line instead  
// template<class T> void Vector<T>::sort() {}  
```