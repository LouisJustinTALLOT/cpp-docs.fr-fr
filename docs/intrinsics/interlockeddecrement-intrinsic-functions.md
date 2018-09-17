---
title: _InterlockedDecrement, fonctions intrinsèques | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _InterlockedDecrement16_rel_cpp
- _InterlockedDecrement16_acq_cpp
- _InterlockedDecrement16_rel
- _InterlockedDecrement64_acq
- _InterlockedDecrement_nf
- _InterlockedDecrement16_nf
- _InterlockedDecrement64_rel_cpp
- _InterlockedDecrement_rel_cpp
- _InterlockedDecrement16_acq
- _InterlockedDecrement64_acq_cpp
- _InterlockedDecrement_rel
- _InterlockedDecrement64_nf
- _InterlockedDecrement16_cpp
- _InterlockedDecrement64
- _InterlockedDecrement_cpp
- _InterlockedDecrement64_rel
- _InterlockedDecrement16
- _InterlockedDecrement
- _InterlockedDecrement64_cpp
- _InterlockedDecrement_acq
- _InterlockedDecrement_acq_cpp
dev_langs:
- C++
helpviewer_keywords:
- InterlockedDecrement64_rel intrinsic
- InterlockedDecrement64 intrinsic
- _InterlockedDecrement16 intrinsic
- _InterlockedDecrement16_acq intrinsic
- _InterlockedDecrement intrinsic
- _InterlockedDecrement_nf intrinsic
- _InterlockedDecrement_acq intrinsic
- _InterlockedDecrement64_rel intrinsic
- _InterlockedDecrement16_rel intrinsic
- InterlockedDecrement intrinsic
- InterlockedDecrement16 intrinsic
- _InterlockedDecrement16_nf intrinsic
- InterlockedDecrement64_acq intrinsic
- _InterlockedDecrement_rel intrinsic
- InterlockedDecrement_acq intrinsic
- _InterlockedDecrement64_acq intrinsic
- _InterlockedDecrement64 intrinsic
- _InterlockedDecrement64_nf intrinsic
- InterlockedDecrement_rel intrinsic
ms.assetid: 5268fce3-86b5-4b2b-b96c-2e531a3fb9b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2bf3f35b4de412125fcaf1c801a044c1b72e3233
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716259"
---
# <a name="interlockeddecrement-intrinsic-functions"></a>_InterlockedDecrement, fonctions intrinsèques
**Section spécifique à Microsoft**  
  
Fournit la prise en charge intrinsèque du compilateur pour le Kit de développement logiciel Windows Win32 [InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement) (fonction).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
long _InterlockedDecrement(  
   long * lpAddend  
);  
long _InterlockedDecrement_acq(  
   long * lpAddend  
);  
long _InterlockedDecrement_rel(  
   long * lpAddend  
);  
long _InterlockedDecrement_nf(  
   long * lpAddend  
);  
short _InterlockedDecrement16(  
   short * lpAddend  
);  
short _InterlockedDecrement16_acq(  
   short * lpAddend  
);  
short _InterlockedDecrement16_rel(  
   short * lpAddend  
);  
short _InterlockedDecrement16_nf(  
   short * lpAddend  
);  
__int64 _InterlockedDecrement64(  
   __int64 * lpAddend  
);  
__int64 _InterlockedDecrement64_acq(  
   __int64 * lpAddend  
);  
__int64 _InterlockedDecrement64_rel(  
   __int64 * lpAddend  
);   
__int64 _InterlockedDecrement64_nf(  
   __int64 * lpAddend  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*lpAddend*<br/>
[in, out] Pointeur vers la variable à décrémenter.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur de retour est la valeur décrémentée résultante.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`_InterlockedDecrement`, `_InterlockedDecrement16`, `_InterlockedDecrement64`|x86, ARM, x64|  
|`_InterlockedDecrement_acq`, `_InterlockedDecrement_rel`, `_InterlockedDecrement_nf`, `_InterlockedDecrement16_acq`, `_InterlockedDecrement16_rel`, `_InterlockedDecrement16_nf`, `_InterlockedDecrement64_acq`, `_InterlockedDecrement64_rel`, `_InterlockedDecrement64_nf`,|ARM|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Il existe plusieurs variantes de `_InterlockedDecrement` qui varient selon les types de données qu'elles impliquent et l'utilisation d'une sémantique acquire ou release spécifique au processeur.  
  
 La fonction `_InterlockedDecrement` opère sur des valeurs entières de 32 bits, `_InterlockedDecrement16` sur des valeurs entières de 16 bits et `_InterlockedDecrement64` sur des valeurs entières de 64 bits.  
  
 Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d'une section critique. Les fonctions intrinsèques avec un suffixe `_nf` (pour « no fence », « pas de délimitation ») n'agissent pas comme une barrière mémoire.  
  
 La variable vers laquelle pointe le paramètre `lpAddend` doit être alignée sur une limite de 32 bits. Dans le cas contraire, cette fonction échoue sur les systèmes x86 multiprocesseurs et les systèmes autres que x86. Pour plus d’informations, consultez [aligner](../cpp/align-cpp.md).  
  
 Ces routines sont disponibles seulement comme fonctions intrinsèques.  
  
## <a name="example"></a>Exemple  
  
```  
// compiler_intrinsics_interlocked.cpp  
// compile with: /Oi  
#define _CRT_RAND_S  
  
#include <cstdlib>  
#include <cstdio>  
#include <process.h>  
#include <windows.h>  
  
// To declare an interlocked function for use as an intrinsic,  
// include intrin.h and put the function in a #pragma intrinsic   
// statement.  
#include <intrin.h>  
  
#pragma intrinsic (_InterlockedIncrement)  
  
// Data to protect with the interlocked functions.  
volatile LONG data = 1;  
  
void __cdecl SimpleThread(void* pParam);  
  
const int THREAD_COUNT = 6;  
  
int main() {  
   DWORD num;  
   HANDLE threads[THREAD_COUNT];  
   int args[THREAD_COUNT];  
   int i;  
  
   for (i = 0; i < THREAD_COUNT; i++) {  
     args[i] = i + 1;  
     threads[i] = reinterpret_cast<HANDLE>(_beginthread(SimpleThread, 0,   
                           args + i));  
      if (threads[i] == reinterpret_cast<HANDLE>(-1))  
         // error creating threads  
         break;  
   }  
  
   WaitForMultipleObjects(i, threads, true, INFINITE);  
}  
  
// Code for our simple thread  
void __cdecl SimpleThread(void* pParam) {  
   int threadNum = *((int*)pParam);  
   int counter;  
   unsigned int randomValue;  
   unsigned int time;  
   errno_t err = rand_s(&randomValue);  
  
   if (err == 0) {  
      time = (unsigned int) ((double) randomValue / (double) UINT_MAX * 500);  
      while (data < 100) {  
         if (data < 100) {  
            _InterlockedIncrement(&data);  
            printf_s("Thread %d: %d\n", threadNum, data);  
         }  
  
         Sleep(time);   // wait up to half of a second  
      }  
   }  
  
   printf_s("Thread %d complete: %d\n", threadNum, data);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [Mots clés](../cpp/keywords-cpp.md)   
 [Conflits avec le compilateur x86](../build/conflicts-with-the-x86-compiler.md)