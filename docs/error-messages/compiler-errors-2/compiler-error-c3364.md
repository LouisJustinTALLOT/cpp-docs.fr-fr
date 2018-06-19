---
title: Erreur du compilateur C3364 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3364
dev_langs:
- C++
helpviewer_keywords:
- C3364
ms.assetid: 98654741-60fe-4472-a6af-e580f8c0a6e1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 337bcf71e89dc1ff3e434eba6645f76df1022a11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257845"
---
# <a name="compiler-error-c3364"></a>Erreur du compilateur C3364
'délégué' : constructeur délégué : l’argument doit être le pointeur vers la fonction membre de classe managée ou une fonction globale  
  
 Le deuxième paramètre de constructeur du délégué prend l’adresse d’une fonction membre ou l’adresse d’une fonction membre statique de n’importe quelle classe. Les deux sont traitées comme des adresses simples.  
  
 L’exemple suivant génère l’erreur C3364 :  
  
```  
// C3364_2.cpp  
// compile with: /clr  
  
delegate int D( int, int );  
  
ref class C {  
public:  
   int mf( int, int ) {  
      return 1;  
   }  
};  
  
int main() {  
   C^ pC = gcnew C;  
   System::Delegate^ pD = gcnew D( pC,pC->mf( 1, 2 ) ); // C3364  
  
   // try the following line instead  
   // System::Delegate^ pD = gcnew D(pC, &C::mf);  
}  
```  
