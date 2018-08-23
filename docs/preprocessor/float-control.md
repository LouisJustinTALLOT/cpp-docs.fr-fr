---
title: float_control | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
dev_langs:
- C++
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b94e5b8eccdc63735c7cb25faa7eacb1e23670
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540801"
---
# <a name="floatcontrol"></a>float_control
Spécifie le comportement de virgule flottante d'une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
float_control( value,setting [push] | push | pop )  
```  
  
## <a name="flags"></a>Indicateurs  
 
*valeur*, *paramètre* *[push]*  
Spécifie le comportement de virgule flottante. *valeur* peut être `precise` ou `except`. Pour plus d’informations, consultez l’article [/fp (Spécifier le comportement de virgule flottante)](../build/reference/fp-specify-floating-point-behavior.md). *paramètre* peut être `on` ou `off`.  
  
Si *valeur* est `precise`, les paramètres pour `precise` et `except` sont spécifiés. `except` peut uniquement être définie sur `on` lorsque `precise` est également défini sur `on`.  
  
Si le paramètre facultatif *push* jeton est ajouté, actuel définissant pour *valeur* est envoyée sur à la pile interne du compilateur.  
  
*push*  
Exécute un push du **float_control** définition sur la pile interne du compilateur  
  
*pop*  
Supprime le **float_control** définition à partir du haut de la pile interne du compilateur et qui rend la nouvelle **float_control** paramètre.  
  
## <a name="remarks"></a>Notes  
 
Vous ne pouvez pas désactiver `float_control precise` lorsque `except` est activé. De même, `precise` ne peut pas être désactivé lorsque `fenv_access` est activé. Pour passer d’un modèle strict à un modèle rapide avec le **float_control** pragma, utilisez le code suivant :  
  
```  
#pragma float_control(except, off)  
#pragma fenv_access(off)  
#pragma float_control(precise, off)  
```  
  
Pour passer d’un modèle rapide à un modèle strict avec le **float_control** pragma, utilisez le code suivant :  
  
```  
#pragma float_control(precise, on)  
#pragma fenv_access(on)  
#pragma float_control(except, on)  
```  
  
Les autres pragmas à virgule flottante incluent :  
  
- [fenv_access](../preprocessor/fenv-access.md)  
  
- [fp_contract](../preprocessor/fp-contract.md)  
  
## <a name="example"></a>Exemple  
 
L’exemple suivant montre comment intercepter une exception de virgule flottante de dépassement de capacité en utilisant le pragma **float_control**.  
  
```cpp  
// pragma_directive_float_control.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <float.h>  
  
double func( ) {  
   return 1.1e75;  
}  
  
#pragma float_control (except,on)  
  
int main( ) {  
   float u[1];  
   unsigned int currentControl;  
   errno_t err;  
  
   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);  
   if (err != 0)  
      printf_s("_controlfp_s failed!\n");  
  
   try  {  
      u[0] = func();  
      printf_s ("Fail");     
      return(1);  
   }   
  
   catch (...)  {  
      printf_s ("Pass");  
      return(0);  
   }  
}  
```  
  
```Output  
Pass  
```  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)  
