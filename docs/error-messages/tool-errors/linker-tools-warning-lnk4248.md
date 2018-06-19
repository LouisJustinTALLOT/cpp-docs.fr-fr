---
title: LNK4248 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4248
dev_langs:
- C++
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e3b67661d1ad260f388f8425420711ae2f708ce3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302631"
---
# <a name="linker-tools-warning-lnk4248"></a>Avertissement des outils Éditeur de liens LNK4248
jeton typeref non résolu (jeton) pour 'type' ; image ne peut pas s’exécuter  
  
 Un type ne possède pas une définition dans les métadonnées MSIL.  
  
 LNK4248 peut se produire lorsqu’il existe uniquement une déclaration anticipée d’un type dans un module MSIL (compilé avec **/CLR**), où le type est référencé dans le module MSIL et où le module MSIL est lié à un module natif possédant une définition pour le type.  
  
 Dans ce cas, l’éditeur de liens fournit la définition de type natif dans les métadonnées MSIL, et cela peut indiquer le comportement correct.  
  
 Toutefois, si une déclaration de type de transfert est un type CLR, puis définition d’un type natif de l’éditeur de liens peut-être pas correcte  
  
 Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Fournir la définition de type dans le module MSIL.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur LNK4248. Définir un struct à résoudre.  
  
```  
// LNK4248.cpp  
// compile with: /clr /W1  
// LNK4248 expected  
struct A;  
void Test(A*){}  
  
int main() {  
   Test(0);  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant comprend une définition anticipée d’un type.  
  
```  
// LNK4248_2.cpp  
// compile with: /clr /c  
class A;   // provide a definition for A here to resolve  
A * newA();  
int valueA(A * a);  
  
int main() {  
   A * a = newA();  
   return valueA(a);  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur LNK4248.  
  
```  
// LNK4248_3.cpp  
// compile with: /c  
// post-build command: link LNK4248_2.obj LNK4248_3.obj  
class A {  
public:   
   int b;  
};  
  
A* newA() {  
   return new A;  
}  
  
int valueA(A * a) {  
   return (int)a;  
}  
```