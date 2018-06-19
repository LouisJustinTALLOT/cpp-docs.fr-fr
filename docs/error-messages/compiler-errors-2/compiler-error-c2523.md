---
title: Erreur du compilateur C2523 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2523
dev_langs:
- C++
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4546e576ced8d57a35c4c4861f29824a8d91d910
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33228339"
---
# <a name="compiler-error-c2523"></a>Erreur du compilateur C2523
' classe :: ~ identificateur ' : incompatibilité de balise de destructeur/finaliseur  
  
 Le nom du destructeur doit être le nom de la classe précédé par un tilde (`~`). Le constructeur et le destructeur sont les seuls les membres qui ont le même nom que la classe.  
  
 L’exemple suivant génère l’erreur C2523 :  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```