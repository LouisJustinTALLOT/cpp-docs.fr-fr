---
title: Erreur du compilateur C3234 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3234
dev_langs:
- C++
helpviewer_keywords:
- C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 10964afb48e4a83830d0eb48a5f2147906a3543e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33246015"
---
# <a name="compiler-error-c3234"></a>Erreur du compilateur C3234
une classe générique ne peut pas dériver d'un paramètre de type générique  
  
 Une classe générique ne peut pas hériter d’un paramètre de type générique.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C3234.  
  
```  
// C3234.cpp  
// compile with: /clr /c  
generic <class T>  
public ref class C : T {};   // C3234  
// try the following line instead  
// public ref class C {};  
```