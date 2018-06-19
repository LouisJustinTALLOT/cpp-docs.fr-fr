---
title: Lock::try_acquire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- try_acquire
- lock.try_acquire
- msclr.lock.try_acquire
- lock::try_acquire
- msclr::lock::try_acquire
dev_langs:
- C++
helpviewer_keywords:
- lock::try_acquire
ms.assetid: ef0649a9-e611-4495-84bd-2784533221d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 25b5ec1ab7bb5c429538f312ee3b598d3d1d83ec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33137508"
---
# <a name="locktryacquire"></a>lock::try_acquire
Acquiert un verrou sur un objet, en attente pour un laps de temps et en retournant un `bool` pour signaler la réussite de l’acquisition au lieu de lever une exception.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
bool try_acquire(  
   int _timeout_ms  
);  
bool try_acquire(  
   System::TimeSpan _timeout  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `_timeout`  
 Valeur de délai d’attente en millisecondes, ou comme un <xref:System.TimeSpan>.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` Si le verrou a été acquis, `false` dans le cas contraire.  
  
## <a name="remarks"></a>Notes  
 Si un verrou a déjà été acquis, cette fonction ne fait rien.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise une seule instance d’une classe sur plusieurs threads.  La classe utilise un verrou sur lui-même pour vous assurer que l’accès à ses données internes sont cohérents pour chaque thread.  Le thread d’application principale utilise un verrou sur la même instance de la classe à vérifier régulièrement si les threads de travail existent toujours, et attend de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.  
  
```  
// msl_lock_try_acquire.cpp  
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
  
## <a name="requirements"></a>Spécifications  
 **Fichier d’en-tête** \<msclr\lock.h >  
  
 **Namespace** msclr  
  
## <a name="see-also"></a>Voir aussi  
 [Lock, membres](../dotnet/lock-members.md)   
 [lock::acquire](../dotnet/lock-acquire.md)