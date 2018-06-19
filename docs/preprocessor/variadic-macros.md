---
title: Macros Variadic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5918c7d91a3568799f361fcb42edb2e9c7b1445e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850533"
---
# <a name="variadic-macros"></a>Macros Variadic
Macros Variadic sont des macros de type fonction contenant un nombre variable d’arguments.  
  
## <a name="remarks"></a>Notes  
 Pour utiliser des macros variadiques, les points de suspension peut être spécifié comme argument formel final dans une définition de macro et l’identificateur de remplacement `__VA_ARGS__` peut être utilisée dans la définition d’insérer les arguments en trop.  `__VA_ARGS__` est remplacé par tous les arguments qui correspondent à des points de suspension, y compris des virgules entre eux.  
  
 La norme du C indique qu’au moins un argument doit être transmis à la sélection, pour vous assurer que la macro n’est pas résolu en une expression avec une virgule de fin.  L’implémentation Visual C++ permettent de supprimer une virgule de fin si aucun argument pour les points de suspension.  
  
## <a name="example"></a>Exemple  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Macros (C/C++)](../preprocessor/macros-c-cpp.md)