---
title: Compilateur avertissement (niveau 3) C4792 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4792
dev_langs:
- C++
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 7886d2b28c9120e2e764dedd0ecc72265fe91be5
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4792"></a>Avertissement du compilateur (niveau 3) C4792
fonction 'function' déclarée à l’aide de sysimport et référencée à partir du code natif ; bibliothèque d’importation requise pour établir la liaison  
  
 Une fonction native qui a été importée dans le programme avec DllImport a été appelée à partir d’une fonction non managée. Vous devez donc établir une liaison à la bibliothèque d’importation pour la DLL.  
  
 Vous ne pouvez pas résoudre cet avertissement en modifiant le code ou le mode de compilation. Utilisez le [avertissement](../../preprocessor/warning.md) pragma pour désactiver cet avertissement.  
  
 L’exemple suivant génère l’avertissement C4792 :  
  
```  
// C4792.cpp  
// compile with: /clr /W3  
// C4792 expected  
using namespace System::Runtime::InteropServices;  
[DllImport("msvcrt")]  
extern "C" int __cdecl puts(const char *);  
int main() {}  
  
// Uncomment the following line to resolve.  
// #pragma warning(disable : 4792)  
#pragma unmanaged  
void func(void){  
   puts("test");  
}  
```
