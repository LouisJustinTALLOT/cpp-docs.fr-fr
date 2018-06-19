---
title: déconseillés (C/C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs:
- C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2280d5245292625bfc29815475eaca63d4d500bd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839817"
---
# <a name="deprecated-cc"></a>deprecated (C/C++)
Le **déconseillée** pragma vous permet d’indiquer qu’une fonction, type ou tout autre identificateur peut ne plus être pris en charge dans une future version ou ne doit plus être utilisé.  
> [!NOTE]
> Pour plus d’informations sur C ++ 14 `[[deprecated]]` attribut et des conseils sur l’utilisation qui attribut vs le declspec de Microsoft ou le pragma, consultez [attributs Standard C++](../cpp/attributes.md) attribut.
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>Notes  
 Lorsque le compilateur rencontre un identificateur spécifié par un **déconseillée** pragma, il émet un avertissement du compilateur [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).   
  
 Vous pouvez désapprouver des noms de macros. Placez le nom de la macro entre guillemets, sinon une expansion macro va se produire.  
  
 Étant donné que la **déconseillée** pragma fonctionne sur tous les identificateurs de correspondance et ne prend pas de signatures en compte, il n’est pas la meilleure option de l’obsolescence des versions spécifiques de fonctions surchargées. N’importe quel nom de la fonction correspondante est placée dans la portée déclenche l’avertissement.

  Nous vous recommandons d’utiliser C ++ 14 `[[deprecated]]` d’attribut, si possible, au lieu du **déconseillée** pragma. Spécifique à Microsoft [__declspec (deprecated)](../cpp/deprecated-cpp.md) modificateur de déclaration est également un meilleur choix dans de nombreux cas que le **déconseillée** pragma. Le `[[deprecated]]` attribut et `__declspec(deprecated)` modificateur permettent de spécifier l’état déconseillé pour les formes spéciales des fonctions surchargées. L’avertissement de diagnostic apparaît uniquement sur les références à la fonction surchargée spécifique l’attribut ou le modificateur s’applique à.  
  
## <a name="example"></a>Exemple  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 L'exemple suivant montre comment déconseiller une classe :  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)