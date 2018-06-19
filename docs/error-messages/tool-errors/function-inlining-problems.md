---
title: Problèmes de fonctions inline | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 670136a61d5991655a5d99e8257c6bcc907f2dfb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300226"
---
# <a name="function-inlining-problems"></a>Problèmes de fonctions inline
Si vous utilisez des fonctions inline, vous devez :  
  
-   Définissez les fonctions inline implémentées dans le fichier d’en-tête inclus.  
  
-   Avoir incorporation (inlining) dans le fichier d’en-tête.  
  
```  
// LNK2019_function_inline.cpp  
// compile with: /c   
// post-build command: lib LNK2019_function_inline.obj  
#include <stdio.h>  
struct _load_config_used {  
   void Test();  
   void Test2() { printf("in Test2\n"); }  
};  
  
void _load_config_used::Test() { printf("in Test\n"); }  
```  
  
 Puis,  
  
```  
// LNK2019_function_inline_2.cpp  
// compile with: LNK2019_function_inline.lib  
struct _load_config_used {  
   void Test();  
   void Test2();  
};  
  
int main() {  
   _load_config_used x;  
   x.Test();  
   x.Test2();   // LNK2019  
}  
```  
  
 Si vous utilisez le `#pragma inline_depth` Vérifiez directive de compilateur que vous avez une valeur de 2 ou plus défini. Une valeur égale à zéro s’éteint incorporation (inlining). Assurez-vous également que vous utilisez le **/Ob1** ou **/Ob2** options du compilateur.  
  
 Panachage d’options de compilation en ligne et non en ligne sur des modules différents peut parfois causer des problèmes. Si une bibliothèque C++ est créée avec la fonctionnalité inline activée ([/Ob1](../../build/reference/ob-inline-function-expansion.md) ou [/Ob2](../../build/reference/ob-inline-function-expansion.md)), mais le fichier d’en-tête correspondant décrivant les fonctions a désactivé cette fonctionnalité (sans option), vous obtiendrez l’erreur LNK2001. Les fonctions n’obtiennent pas inline dans le code à partir du fichier d’en-tête, mais qui ne sont pas dans le fichier de bibliothèque aucune adresse pour résoudre la référence est.  
  
 De même, un projet qui utilise la fonction inline mais définit les fonctions dans un fichier .cpp au plutôt que dans l’en-tête de fichier obtiendra également l’erreur LNK2019. Le fichier d’en-tête est inclus partout semble approprié, mais les fonctions sont uniquement inline lorsque le fichier .cpp passe par le compilateur ; Par conséquent, l’éditeur de liens voit les fonctions comme externes non résolus lorsqu’il est utilisé dans d’autres modules.  
  
```  
// LNK2019_FIP.h  
struct testclass {  
   void PublicStatMemFunc1(void);  
};  
```  
  
 Et puis  
  
```  
// LNK2019_FIP.cpp  
// compile with: /c  
#include "LNK2019_FIP.h"  
inline void testclass::PublicStatMemFunc1(void) {}  
```  
  
 Et puis  
  
```  
// LNK2019_FIP_2.cpp  
// compile with: LNK2019_FIP.cpp  
// LNK2019 expected  
#include "LNK2019_FIP.h"  
int main() {  
   testclass testclsObject;  
  
   // module cannot see the implementation of PublicStatMemFunc1  
   testclsObject.PublicStatMemFunc1();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)