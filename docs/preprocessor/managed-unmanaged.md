---
title: managé, non managé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
dev_langs:
- C++
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316866ac047b607ec4c92d7c6d4f8ff233ed9a3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846374"
---
# <a name="managed-unmanaged"></a>managé, non managé
Activez le contrôle au niveau de la fonction pour compiler les fonctions comme managées ou non managées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #pragma managed  
#pragma unmanaged  
#pragma managed([push,] on | off)  
#pragma managed(pop)  
```  
  
## <a name="remarks"></a>Notes  
 Le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur fournit le contrôle au niveau du module pour compiler les fonctions comme managées ou non managées.  
  
 Une fonction non managée est compilée pour la plateforme native et l'exécution de cette partie du programme est passée à la plateforme native par le Common Langage Runtime.  
  
 Les fonctions sont compilées comme managées par défaut lorsque **/CLR** est utilisé.  
  
 Quand vous appliquez ces pragmas :  
  
-   Ajoutez le pragma devant une fonction, et non dans un corps de fonction.  
  
-   Ajoutez le pragma après les instructions `#include`. N'utilisez pas ces pragmas avant les instructions `#include`.  
  
 Le compilateur ignore le `managed` et `unmanaged` pragmas si **/CLR** n’est pas utilisé dans la compilation.  
  
 Lorsqu'une fonction modèle est instanciée, l'état du pragma au moment de la définition du modèle détermine si elle est managée ou non managée.  
  
 Pour plus d’informations, consultez [l’initialisation d’assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md).  
  
## <a name="example"></a>Exemple  
  
```cpp  
// pragma_directives_managed_unmanaged.cpp  
// compile with: /clr  
#include <stdio.h>  
  
// func1 is managed  
void func1() {  
   System::Console::WriteLine("In managed function.");  
}  
  
// #pragma unmanaged  
// push managed state on to stack and set unmanaged state  
#pragma managed(push, off)  
  
// func2 is unmanaged  
void func2() {  
   printf("In unmanaged function.\n");  
}  
  
// #pragma managed  
#pragma managed(pop)  
  
// main is managed  
int main() {  
   func1();  
   func2();  
}  
```  
  
```Output  
In managed function.  
In unmanaged function.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)