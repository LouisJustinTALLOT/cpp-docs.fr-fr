---
title: Erreur du compilateur C3266 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3266
dev_langs:
- C++
helpviewer_keywords:
- C3266
ms.assetid: 7375c099-acb7-42f6-898d-57cfefa010b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52c6cc27c6724f5709ae4ded984afff23d16e19c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247821"
---
# <a name="compiler-error-c3266"></a>Erreur du compilateur C3266
'classe' : un constructeur de classe doit avoir une liste de paramètres 'void'  
  
Les constructeurs de classe dans une classe qui utilise la programmation /clr ne peuvent pas prendre de paramètres.  
  
L’exemple suivant génère l’erreur C3266 :  
  
```  
// C3266.cpp  
// compile with: /clr  
  
ref class X {  
   static X(int i) { // C3266  
   // try the following line instead  
   // static X() {  
   }  
};  
  
int main() {  
}  
```  
