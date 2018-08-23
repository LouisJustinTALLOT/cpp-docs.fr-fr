---
title: _AddressOfReturnAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b0b259c730a7db343cc08ff077cf57043f292a6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540818"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress
**Section spécifique à Microsoft**  
  
 Fournit l’adresse de l’emplacement de mémoire qui contient l’adresse de retour de la fonction active. Cette adresse ne peut pas être utilisée pour accéder aux autres emplacements de mémoire (par exemple, les arguments de la fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void * _AddressOfReturnAddress();  
```  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_AddressOfReturnAddress`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Lorsque `_AddressOfReturnAddress` est utilisée dans un programme compilé avec [/CLR](../build/reference/clr-common-language-runtime-compilation.md), la fonction contenant le `_AddressOfReturnAddress` appel est compilé en tant qu’une fonction native. Quand une fonction compilée comme géré appelle la fonction contenant `_AddressOfReturnAddress`, `_AddressOfReturnAddress` ne peut pas fonctionner comme prévu.  
  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
## <a name="example"></a>Exemple  
  
```  
// compiler_intrinsics_AddressOfReturnAddress.cpp  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
// This function will print three values:  
//   (1) The address retrieved from _AddressOfReturnAdress  
//   (2) The return address stored at the location returned in (1)  
//   (3) The return address retrieved the _ReturnAddress* intrinsic  
// Note that (2) and (3) should be the same address.  
__declspec(noinline)  
void func() {  
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();  
   printf_s("%p\n", pvAddressOfReturnAddress);  
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));  
   printf_s("%p\n", _ReturnAddress());  
}  
  
int main() {  
   func();  
}  
```  
  
```Output  
0012FF78  
00401058  
00401058  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Mots clés](../cpp/keywords-cpp.md)