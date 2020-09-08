---
title: _InterlockedDecrement fonctions intrinsèques
description: Fonctions intrinsèques du compilateur Microsoft C/C++ pour la décrémentation verrouillée.
ms.date: 09/03/2020
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
ms.openlocfilehash: b3ca624ba54f70750ecc303fb44f4fa242b4edc2
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556332"
---
# <a name="_interlockeddecrement-intrinsic-functions"></a>`_InterlockedDecrement` fonctions intrinsèques

Fournit la prise en charge intrinsèque du compilateur pour la fonction Win32 SDK Windows [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement) . Les `_InterlockedDecrement` fonctions intrinsèques sont **spécifiques à Microsoft**.

## <a name="syntax"></a>Syntaxe

```C
long _InterlockedDecrement(
   long volatile * lpAddend
);
long _InterlockedDecrement_acq(
   long volatile * lpAddend
);
long _InterlockedDecrement_rel(
   long volatile * lpAddend
);
long _InterlockedDecrement_nf(
   long volatile * lpAddend
);
short _InterlockedDecrement16(
   short volatile * lpAddend
);
short _InterlockedDecrement16_acq(
   short volatile * lpAddend
);
short _InterlockedDecrement16_rel(
   short volatile * lpAddend
);
short _InterlockedDecrement16_nf(
   short volatile * lpAddend
);
__int64 _InterlockedDecrement64(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_acq(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_rel(
   __int64 volatile * lpAddend
);
__int64 _InterlockedDecrement64_nf(
   __int64 volatile * lpAddend
);
```

### <a name="parameters"></a>Paramètres

*lpAddend*\
[in, out] Pointeur volatil vers la variable à décrémenter.

## <a name="return-value"></a>Valeur renvoyée

La valeur de retour est la valeur décrémentée résultante.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`_InterlockedDecrement`, `_InterlockedDecrement16`|x86, ARM, x64, ARM64|
|`_InterlockedDecrement64`|ARM, x64, ARM64|
|`_InterlockedDecrement_acq`, `_InterlockedDecrement_rel`, `_InterlockedDecrement_nf`, `_InterlockedDecrement16_acq`, `_InterlockedDecrement16_rel`, `_InterlockedDecrement16_nf`, `_InterlockedDecrement64_acq`, `_InterlockedDecrement64_rel`, `_InterlockedDecrement64_nf`,|ARM, ARM64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Il existe plusieurs variantes de `_InterlockedDecrement` qui varient selon les types de données qu’elles impliquent et l’utilisation d’une sémantique acquire ou release spécifique au processeur.

La fonction `_InterlockedDecrement` opère sur des valeurs entières de 32 bits, `_InterlockedDecrement16` sur des valeurs entières de 16 bits et `_InterlockedDecrement64` sur des valeurs entières de 64 bits.

Sur les plateformes ARM, utilisez les fonctions intrinsèques avec des suffixes `_acq` et `_rel` si vous devez acquérir et libérer des éléments de la sémantique, comme le début et la fin d’une section critique. Les intrinsèques avec un `_nf` suffixe (« no cloture ») n’agissent pas comme une barrière de mémoire.

La variable vers laquelle pointe le paramètre `lpAddend` doit être alignée sur une limite de 32 bits. Dans le cas contraire, cette fonction échoue sur les systèmes x86 multiprocesseurs et les systèmes autres que x86. Pour plus d’informations, consultez [Aligner](../cpp/align-cpp.md).

Ces routines sont disponibles seulement comme fonctions intrinsèques.

## <a name="example"></a>Exemple

```cpp
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

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mot](../cpp/keywords-cpp.md)\
[Conflits avec le compilateur x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
