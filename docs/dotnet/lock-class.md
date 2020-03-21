---
title: lock, classe
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- msclr::lock::lock
- msclr::lock::is_locked
- msclr::lock.is_locked
- msclr::lock::acquire
- msclr::lock::try_acquire
- msclr::lock::release
- msclr::lock::operator==
- msclr::lock::operator!=
helpviewer_keywords:
- msclr::lock class
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
ms.openlocfilehash: b2ae1be31233e55aa34d6f3046d90fb2127348c0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80080041"
---
# <a name="lock-class"></a>lock, classe

Cette classe automatise la création d’un verrou pour synchroniser l’accès à un objet à partir de plusieurs threads.  Lorsqu’il est construit, il acquiert le verrou et, lorsqu’il est détruit, il libère le verrou.

## <a name="syntax"></a>Syntaxe

```cpp
ref class lock;
```

## <a name="remarks"></a>Notes

`lock` est disponible uniquement pour les objets CLR et ne peut être utilisé que dans du code CLR.

En interne, la classe Lock utilise <xref:System.Threading.Monitor> pour synchroniser l’accès. Pour plus d’informations, consultez l’article référencé.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|---------|-----------|
|[lock::lock](#lock)|Construit un objet `lock`, en attendant éventuellement à acquérir définitivement le verrou, pendant un laps de temps spécifié, ou pas du tout.|
|[lock::~lock](#tilde-lock)|Détruit un objet `lock`.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|---------|-----------|
|[lock::acquire](#acquire)|Acquiert un verrou sur un objet, en attendant éventuellement acquérir le verrou indéfiniment, pendant un laps de temps spécifié, ou pas du tout.|
|[lock::is_locked](#is-locked)|Indique si un verrou est maintenu.|
|[lock::release](#release)|Libère un verrou.|
|[lock::try_acquire](#try-acquire)|Acquiert un verrou sur un objet, en attente d’un laps de temps spécifié et en retournant un `bool` pour signaler la réussite de l’acquisition au lieu de lever une exception.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|---------|-----------|
|[Lock :: Operator&nbsp;bool](#operator-bool)|Opérateur permettant d’utiliser `lock` dans une expression conditionnelle.|
|[lock::operator==](#operator-equality)|Opérateur d’égalité.|
|[lock::operator!=](#operator-inequality)|Opérateur d’inégalité.|

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr\lock.h >

**Espace de noms** msclr,

## <a name="locklock"></a><a name="lock"></a>verrou :: Lock

Construit un objet `lock`, en attendant éventuellement à acquérir définitivement le verrou, pendant un laps de temps spécifié, ou pas du tout.

```cpp
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

### <a name="parameters"></a>Paramètres

*_object*<br/>
Objet à verrouiller.

*_timeout*<br/>
Valeur de délai d’attente en millisecondes ou en tant que <xref:System.TimeSpan>.

### <a name="exceptions"></a>Exceptions

Lève <xref:System.ApplicationException> si l’acquisition de verrous ne se produit pas avant l’expiration du délai d’attente.

### <a name="remarks"></a>Notes

Les trois premières formes du constructeur essaient d’acquérir un verrou sur `_object` dans le délai d’attente spécifié (ou <xref:System.Threading.Timeout.Infinite> si aucune valeur n’est spécifiée).

La quatrième forme du constructeur n’acquiert pas de verrou sur `_object`. `lock_later` est membre de l' [énumération lock_when](../dotnet/lock-when-enum.md). Utilisez [Lock :: Acquire](../dotnet/lock-acquire.md) ou [lock :: try_acquire](../dotnet/lock-try-acquire.md) pour acquérir le verrou dans ce cas.

Le verrou est libéré automatiquement lorsque le destructeur est appelé.

`_object` ne peut pas être <xref:System.Threading.ReaderWriterLock>.  Si c’est le cas, une erreur de compilation se produit.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads. La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent encore. L’application principale attend ensuite de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
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

## <a name="locklock"></a><a name="tilde-lock"></a>verrou :: ~ Lock

Détruit un objet `lock`.

```cpp
~lock();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [Lock :: Release](../dotnet/lock-release.md).

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread.  Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent encore. L’application principale attend ensuite de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
// msl_lock_dtor.cpp
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

## <a name="lockacquire"></a><a name="acquire"></a>Lock :: Acquire

Acquiert un verrou sur un objet, en attendant éventuellement acquérir le verrou indéfiniment, pendant un laps de temps spécifié, ou pas du tout.

```cpp
void acquire();
void acquire(
   int _timeout
);
void acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Paramètres

*_timeout*<br/>
Valeur de délai d’attente en millisecondes ou en tant que <xref:System.TimeSpan>.

### <a name="exceptions"></a>Exceptions

Lève <xref:System.ApplicationException> si l’acquisition de verrous ne se produit pas avant l’expiration du délai d’attente.

### <a name="remarks"></a>Notes

Si une valeur de délai d’attente n’est pas fournie, le délai d’attente par défaut est <xref:System.Threading.Timeout.Infinite>.

Si un verrou a déjà été acquis, cette fonction ne fait rien.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent encore. L’application principale attend ensuite de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
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

## <a name="lockis_locked"></a><a name="is-locked"></a>Lock :: is_locked

Indique si un verrou est maintenu.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Valeur retournée

`true` si un verrou est maintenu, `false` dans le cas contraire.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread.  Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent toujours, et attend de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
// msl_lock_is_locked.cpp
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
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l.is_locked()) { // check if we got the lock
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
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>Lock ::, opérateur bool

Opérateur permettant d’utiliser `lock` dans une expression conditionnelle.

```cpp
operator bool();
```

### <a name="return-value"></a>Valeur retournée

`true` si un verrou est maintenu, `false` dans le cas contraire.

### <a name="remarks"></a>Notes

Cet opérateur convertit en fait `_detail_class::_safe_bool` qui est plus sûr que `bool`, car il ne peut pas être converti en type intégral.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent encore. L’application principale attend de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
// msl_lock_op_bool.cpp
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
      l.try_acquire(50); // try to acquire lock, don't throw an exception if can't
      if (l) { // use bool operator to check for lock
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

## <a name="lockrelease"></a><a name="release"></a>Lock :: Release

Libère un verrou.

```cpp
void release();
```

### <a name="remarks"></a>Notes

Si aucun verrou n’est maintenu, `release` ne fait rien.

Vous n’avez pas besoin d’appeler cette fonction explicitement. Lorsqu’un objet `lock` est hors de portée, son destructeur appelle `release`.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads. La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent encore. L’application principale attend ensuite de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
// msl_lock_release.cpp
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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>Lock :: try_acquire

Acquiert un verrou sur un objet, en attente d’un laps de temps spécifié et en retournant un `bool` pour signaler la réussite de l’acquisition au lieu de lever une exception.

```cpp
bool try_acquire(
   int _timeout_ms
);
bool try_acquire(
   System::TimeSpan _timeout
);
```

### <a name="parameters"></a>Paramètres

*_timeout*<br/>
Valeur de délai d’attente en millisecondes ou en tant que <xref:System.TimeSpan>.

### <a name="return-value"></a>Valeur retournée

`true` si le verrou a été acquis, `false` dans le cas contraire.

### <a name="remarks"></a>Notes

Si un verrou a déjà été acquis, cette fonction ne fait rien.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe sur plusieurs threads. La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le thread d’application principal utilise un verrou sur la même instance de la classe pour vérifier périodiquement si des threads de travail existent encore. L’application principale attend ensuite de quitter jusqu’à ce que tous les threads de travail aient terminé leurs tâches.

```cpp
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

## <a name="lockoperator"></a><a name="operator-equality"></a>Lock :: Operator = =

Opérateur d’égalité.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
Objet dont l'égalité doit être comparée.

### <a name="return-value"></a>Valeur retournée

Retourne `true` si `t` est identique à l’objet du verrou, `false` dans le cas contraire.

### <a name="example"></a>Exemple

```cpp
// msl_lock_op_eq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   lock l1(o1);
   if (l1 == o1) {
      Console::WriteLine("Equal!");
   }
}
```

```Output
Equal!
```

## <a name="lockoperator"></a><a name="operator-inequality"></a>Lock :: Operator ! =

Opérateur d’inégalité.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
Objet à comparer pour déterminer s’il est inégal.

### <a name="return-value"></a>Valeur retournée

Retourne `true` si `t` diffère de l’objet du verrou, `false` dans le cas contraire.

### <a name="example"></a>Exemple

```cpp
// msl_lock_op_ineq.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

int main () {
   Object^ o1 = gcnew Object;
   Object^ o2 = gcnew Object;
   lock l1(o1);
   if (l1 != o2) {
      Console::WriteLine("Inequal!");
   }
}
```

```Output
Inequal!
```