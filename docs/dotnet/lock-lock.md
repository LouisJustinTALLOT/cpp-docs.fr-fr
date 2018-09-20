---
title: Lock::lock | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
dev_langs:
- C++
helpviewer_keywords:
- lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 76991eb9910e046ecdb76f3f169f7d410b38288e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428733"
---
# <a name="locklock"></a>lock::lock

Construit un `lock` objet, si vous le souhaitez attend pour acquérir le verrou d’indéfiniment, pour une durée spécifiée, ou pas du tout.

## <a name="syntax"></a>Syntaxe

```
template<class T> lock(
   T ^ _object
);
template<class T> lock(
   T ^ _object,
   int _timeout
);
template<class T> lock(
   T ^ _object,
   System::TimeSpan _timeout
);
template<class T> lock(
   T ^ _object,
   lock_later
);
```

#### <a name="parameters"></a>Paramètres

*_Object*<br/>
L’objet à verrouiller.

*_délai*<br/>
Valeur de délai d’attente en millisecondes, ou comme un <xref:System.TimeSpan>.

## <a name="exceptions"></a>Exceptions

Lève <xref:System.ApplicationException> si l’acquisition de verrou n’a pas lieu avant le délai d’attente.

## <a name="remarks"></a>Notes

Les trois premiers écrans du constructeur tentent d’acquérir un verrou sur `_object` dans le délai spécifié (ou <xref:System.Threading.Timeout.Infinite> si aucun n’est spécifié).

La quatrième forme du constructeur n’acquiert pas un verrou sur `_object`. `lock_later` est un membre de la [lock_when, Enum](../dotnet/lock-when-enum.md). Utilisez [lock::acquire](../dotnet/lock-acquire.md) ou [lock::try_acquire](../dotnet/lock-try-acquire.md) d’acquérir le verrou dans ce cas.

Le verrou est automatiquement libéré lorsque le destructeur est appelé.

`_object` ne peut pas avoir la valeur <xref:System.Threading.ReaderWriterLock>.  Dans le cas, une erreur de compilateur se produit.

## <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre plusieurs threads.  La classe utilise un verrou sur lui-même pour vous assurer que l’accès à ses données internes sont cohérents pour chaque thread.  Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours et attentes pour quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

```
// msl_lock_lock.cpp
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
[lock::~lock](../dotnet/lock-tilde-lock.md)<br/>
[lock::acquire](../dotnet/lock-acquire.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)