---
title: lock::acquire
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock::acquire
- acquire
- msclr.lock.acquire
- msclr::lock::acquire
- lock.acquire
helpviewer_keywords:
- acquire method
ms.assetid: c214274e-7519-4739-82aa-91b04a32d3f9
ms.openlocfilehash: a799f934024def40c2003f8496b2457d12eb69bf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533729"
---
# <a name="lockacquire"></a>lock::acquire

Acquiert un verrou sur un objet, si vous le souhaitez attend pour acquérir le verrou d’indéfiniment, pour une durée spécifiée, ou pas du tout.

## <a name="syntax"></a>Syntaxe

```
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

#### <a name="parameters"></a>Paramètres

*_délai*<br/>
Valeur de délai d’attente en millisecondes, ou comme un <xref:System.TimeSpan>.

## <a name="exceptions"></a>Exceptions

Lève <xref:System.ApplicationException> si l’acquisition de verrou n’a pas lieu avant le délai d’attente.

## <a name="remarks"></a>Notes

Si une valeur de délai d’expiration n’est pas fournie, le délai d’expiration par défaut est <xref:System.Threading.Timeout.Infinite>.

Si un verrou a déjà été acquis, cette fonction ne fait rien.

## <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre plusieurs threads.  La classe utilise un verrou sur lui-même pour vous assurer que l’accès à ses données internes sont cohérents pour chaque thread.  Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours et attentes pour quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

```
// msl_lock_acquire.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="requirements"></a>Configuration requise

**Fichier d’en-tête** \<msclr\lock.h >

**Namespace** msclr

## <a name="see-also"></a>Voir aussi

[lock, membres](../dotnet/lock-members.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)