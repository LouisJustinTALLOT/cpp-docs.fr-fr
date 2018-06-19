---
title: Du compilateur (niveau 1) d’avertissement C4002 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4002
dev_langs:
- C++
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa1943000becde663fbb0da445f861f408f01f9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272010"
---
# <a name="compiler-warning-level-1-c4002"></a>Avertissement du compilateur (niveau 1) C4002
trop de paramètres réels pour la macro 'identifier'  
  
 Le nombre de paramètres réels dans la macro dépasse le nombre de paramètres formels dans la définition de macro. Le préprocesseur collecte les paramètres supplémentaires mais les ignore pendant l’expansion macro.  
  
 L’avertissement C4002 peut se produire en cas d’utilisation incorrecte de [Variadic Macros](../../preprocessor/variadic-macros.md).  
  
 L’exemple suivant génère l’avertissement C4002 :  
  
```  
// C4002.cpp  
// compile with: /W1  
#define test(a) (a)  
  
int main() {  
   int a = 1;  
   int b = 2;  
   a = test(a,b);   // C4002  
   // try..  
   a = test(a);  
}  
```  
  
 Cette erreur peut également être générée en raison de la mise en conformité du compilateur pour Visual Studio .NET 2003 : les virgules superflues dans la macro ne sont plus acceptées.  
  
 Le compilateur n’accepte plus les virgules superflues dans une macro. Pour que le code soit valide dans les versions Visual Studio .NET 2003 et Visual Studio .NET de Visual C++, supprimez les virgules superflues.  
  
```  
// C4002b.cpp  
// compile with: /W1  
#define F(x,y)  
int main()  
{  
   F(2,,,,,,3,,,,,,)   // C4002  
   // Try the following line instead:  
   // F(2,3)  
}  
```