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
ms.openlocfilehash: 43418da36aa2d87608a9d672e4345d24011be0b3
ms.sourcegitcommit: 9813e146a4eb30929d8352872859e8fcb7ff6d2f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805953"
---
# <a name="lock-class"></a>lock, classe

Cette classe automatise l’acquisition d’un verrou de synchroniser l’accès à un objet à partir de plusieurs threads.  Lorsqu’il est construit il acquiert le verrou et lorsqu’il détruit les versions le verrou.

## <a name="syntax"></a>Syntaxe

```cpp
ref class lock;
```

## <a name="remarks"></a>Notes

`lock` est disponible uniquement pour les objets CLR et peut uniquement être utilisé dans le code CLR.

En interne, la classe du verrou utilise <xref:System.Threading.Monitor> pour synchroniser l’accès. Pour plus d’informations, consultez l’article référencé.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|---------|-----------|
|[lock::lock](#lock)|Construit un `lock` objet, si vous le souhaitez attend pour acquérir le verrou d’indéfiniment, pour une durée spécifiée, ou pas du tout.|
|[lock::~lock](#tilde-lock)|Résulte une `lock` objet.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|---------|-----------|
|[lock::acquire](#acquire)|Acquiert un verrou sur un objet, si vous le souhaitez attend pour acquérir le verrou d’indéfiniment, pour une durée spécifiée, ou pas du tout.|
|[lock::is_locked](#is-locked)|Indique si un verrou est actuellement.|
|[lock::release](#release)|Libère un verrou.|
|[lock::try_acquire](#try-acquire)|Acquiert un verrou sur un objet, en attente pour un laps de temps et en retournant un `bool` pour signaler la réussite de l’acquisition au lieu de lever une exception.|

### <a name="public-operators"></a>Opérateurs publics

|Name|Description|
|---------|-----------|
|[lock::operator&nbsp;bool](#operator-bool)|Opérateur pour l’utilisation de `lock` dans une expression conditionnelle.|
|[lock::operator==](#operator-equality)|Opérateur d’égalité.|
|[lock::operator!=](#operator-inequality)|Opérateur d’inégalité.|

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr\lock.h >

**Namespace** msclr



## <a name="lock"></a>lock::lock

Construit un `lock` objet, si vous le souhaitez attend pour acquérir le verrou d’indéfiniment, pour une durée spécifiée, ou pas du tout.

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
L’objet à verrouiller.

*_timeout*<br/>
Valeur de délai d’expiration en millisecondes, ou comme un <xref:System.TimeSpan>.

### <a name="exceptions"></a>Exceptions

Lève <xref:System.ApplicationException> si l’acquisition de verrou ne se produit avant le délai d’attente.

### <a name="remarks"></a>Notes

Les trois premiers écrans du constructeur essayer d’acquérir un verrou sur `_object` dans le délai spécifié (ou <xref:System.Threading.Timeout.Infinite> si aucun n’est spécifié).

La quatrième forme du constructeur n’acquiert un verrou sur `_object`. `lock_later` est un membre de la [lock_when (enum)](../dotnet/lock-when-enum.md). Utilisez [lock::acquire](../dotnet/lock-acquire.md) ou [lock::try_acquire](../dotnet/lock-try-acquire.md) d’acquérir le verrou dans ce cas.

Le verrou est automatiquement libéré lorsque le destructeur est appelé.

`_object` ne peut pas être <xref:System.Threading.ReaderWriterLock>.  Dans le cas, une erreur de compilateur se produit.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads. La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread. Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours. L’application principale puis attend avant de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="tilde-lock"></a>verrou :: ~ lock

Résulte une `lock` objet.

```cpp
~lock();
```

### <a name="remarks"></a>Notes

Le destructeur appelle [lock::release](../dotnet/lock-release.md).

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads.  La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread.  Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours. L’application principale puis attend avant de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="acquire"></a>lock::acquire

Acquiert un verrou sur un objet, si vous le souhaitez attend pour acquérir le verrou d’indéfiniment, pour une durée spécifiée, ou pas du tout.

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
Valeur de délai d’attente en millisecondes, ou comme un <xref:System.TimeSpan>.

### <a name="exceptions"></a>Exceptions

Lève <xref:System.ApplicationException> si l’acquisition de verrou ne se produit avant le délai d’attente.

### <a name="remarks"></a>Notes

Si une valeur de délai d’expiration n’est pas fournie, le délai d’expiration par défaut est <xref:System.Threading.Timeout.Infinite>.

Si un verrou a déjà été acquis, cette fonction ne fait rien.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads.  La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread. Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours. L’application principale puis attend avant de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="is-locked"></a>lock::is_locked

Indique si un verrou est actuellement.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Valeur de retour

`true` Si un verrou est maintenu, `false` dans le cas contraire.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads.  La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread.  Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours et attentes pour quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="operator-bool"></a>Lock::operator bool

Opérateur pour l’utilisation de `lock` dans une expression conditionnelle.

```cpp
operator bool();
```

### <a name="return-value"></a>Valeur de retour

`true` Si un verrou est maintenu, `false` dans le cas contraire.

### <a name="remarks"></a>Notes

Cet opérateur convertit effectivement `_detail_class::_safe_bool` qui est plus sûr que `bool` , car il ne peut pas être converti en un type intégral.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads.  La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread. Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours. L’application principale attend avant de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="release"></a>lock::release

Libère un verrou.

```cpp
void release();
```

### <a name="remarks"></a>Notes

Si aucun verrou, `release` ne fait rien.

Vous n’êtes pas obligé d’appeler cette fonction explicitement. Quand un `lock` objet est hors de portée, son destructeur appelle `release`.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads. La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread. Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours. L’application principale puis attend avant de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="try-acquire"></a>lock::try_acquire

Acquiert un verrou sur un objet, en attente pour un laps de temps et en retournant un `bool` pour signaler la réussite de l’acquisition au lieu de lever une exception.

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
Valeur de délai d’attente en millisecondes, ou comme un <xref:System.TimeSpan>.

### <a name="return-value"></a>Valeur de retour

`true` Si le verrou a été acquis, `false` dans le cas contraire.

### <a name="remarks"></a>Notes

Si un verrou a déjà été acquis, cette fonction ne fait rien.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe entre les différents threads. La classe utilise un verrou sur lui-même pour s’assurer que l’accès à ses données internes sont cohérents pour chaque thread. Le thread principal de l’application utilise un verrou sur la même instance de la classe pour vérifier périodiquement pour voir si les threads de travail existent toujours. L’application principale puis attend avant de quitter jusqu'à ce que tous les threads de travail ont terminé leurs tâches.

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

## <a name="operator-equality"></a>lock::operator==

Opérateur d’égalité.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
Objet à comparer pour l’égalité.

### <a name="return-value"></a>Valeur de retour

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

## <a name="operator-inequality"></a>lock::operator!=

Opérateur d’inégalité.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Paramètres

*t*<br/>
L’objet pour lequel comparer l’inégalité.

### <a name="return-value"></a>Valeur de retour

Retourne `true` si `t` diffère, objet du verrou, `false` dans le cas contraire.

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