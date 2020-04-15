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
ms.openlocfilehash: ea09dd3d4a2eaf4cf7708d09509cfecfa4a6c6d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373074"
---
# <a name="lock-class"></a>lock, classe

Cette classe automatise la prise d’un verrou pour synchroniser l’accès à un objet à partir de plusieurs threads.  Lorsqu’il est construit, il acquiert la serrure et lorsqu’il est détruit, il libère la serrure.

## <a name="syntax"></a>Syntaxe

```cpp
ref class lock;
```

## <a name="remarks"></a>Notes

`lock`n’est disponible que pour les objets CLR et ne peut être utilisé que dans le code CLR.

En interne, la <xref:System.Threading.Monitor> classe de verrouillage utilise pour synchroniser l’accès. Pour plus d’informations, voir l’article référencé.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|---------|-----------|
|[lock::lock](#lock)|Construit un `lock` objet, en attente d’acquérir la serrure pour toujours, pour une durée spécifiée, ou pas du tout.|
|[serrure: :-lock](#tilde-lock)|Destruction d’un `lock` objet.|

### <a name="public-methods"></a>Méthodes publiques

|Nom|Description|
|---------|-----------|
|[lock::acquire](#acquire)|Acquiert un verrou sur un objet, en attente d’acquisition de la serrure pour toujours, pour un temps spécifié, ou pas du tout.|
|[lock::is_locked](#is-locked)|Indique si un verrou est en cours.|
|[lock::release](#release)|Libère une serrure.|
|[lock::try_acquire](#try-acquire)|Acquiert un verrou sur un objet, en attente `bool` d’un temps spécifié et en retournant un pour signaler le succès de l’acquisition au lieu de jeter une exception.|

### <a name="public-operators"></a>Opérateurs publics

|Nom|Description|
|---------|-----------|
|[serrure::opérateur&nbsp;bool](#operator-bool)|Opérateur pour `lock` l’utilisation dans une expression conditionnelle.|
|[lock::operator==](#operator-equality)|Opérateur d’égalité.|
|[serrure::opérateur!](#operator-inequality)|Opérateur d’inégalité.|

## <a name="requirements"></a>Spécifications

**Fichier d’en-tête** \<msclr-lock.h>

**Namespace** msclr

## <a name="locklock"></a><a name="lock"></a>serrure::lock

Construit un `lock` objet, en attente d’acquérir la serrure pour toujours, pour une durée spécifiée, ou pas du tout.

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
Temps d’une valeur en <xref:System.TimeSpan>millisecondes ou en .

### <a name="exceptions"></a>Exceptions

Les <xref:System.ApplicationException> lancers si l’acquisition de verrouillage ne se produit pas avant le délai d’attente.

### <a name="remarks"></a>Notes

Les trois premières formes du constructeur tentent `_object` d’obtenir un verrou <xref:System.Threading.Timeout.Infinite> dans la période de délai spécifié (ou si aucune n’est spécifiée).

La quatrième forme du constructeur n’acquiert pas de serrure. `_object` `lock_later`est membre de [l’enum lock_when](../dotnet/lock-when-enum.md). Utilisez [le verrou : : acquérir](../dotnet/lock-acquire.md) ou verrouiller : : [try_acquire](../dotnet/lock-try-acquire.md) d’acquérir la serrure dans ce cas.

Le verrou sera automatiquement libéré lorsque le destructeur est appelé.

`_object`ne peut <xref:System.Threading.ReaderWriterLock>pas être .  Si c’est le cas, une erreur de compilateur en résultera.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads. La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours. L’application principale attend alors de sortir jusqu’à ce que tous les fils de travailleur aient terminé leurs tâches.

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

## <a name="locklock"></a><a name="tilde-lock"></a>serrure: :-lock

Destruction d’un `lock` objet.

```cpp
~lock();
```

### <a name="remarks"></a>Notes

Le destructor appelle [le verrou::release](../dotnet/lock-release.md).

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread.  Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours. L’application principale attend alors de sortir jusqu’à ce que tous les fils de travailleur aient terminé leurs tâches.

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

## <a name="lockacquire"></a><a name="acquire"></a>serrure::acquire

Acquiert un verrou sur un objet, en attente d’acquisition de la serrure pour toujours, pour un temps spécifié, ou pas du tout.

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
Valeur de temps en millisecondes ou en tant que <xref:System.TimeSpan>.

### <a name="exceptions"></a>Exceptions

Les <xref:System.ApplicationException> lancers si l’acquisition de verrouillage ne se produit pas avant le délai d’attente.

### <a name="remarks"></a>Notes

Si une valeur de délai d’attente n’est pas fournie, le délai d’attente par défaut est <xref:System.Threading.Timeout.Infinite>.

Si un verrou a déjà été acquis, cette fonction ne fait rien.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours. L’application principale attend alors de sortir jusqu’à ce que tous les fils de travailleur aient terminé leurs tâches.

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

## <a name="lockis_locked"></a><a name="is-locked"></a>serrure::is_locked

Indique si un verrou est en cours.

```cpp
bool is_locked();
```

### <a name="return-value"></a>Valeur retournée

`true`si une serrure `false` est tenue, sinon.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread.  Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours, et attend de sortir jusqu’à ce que tous les fils de travailleur ont terminé leurs tâches.

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

## <a name="lockoperator-bool"></a><a name="operator-bool"></a>serrure::opérateur bool

Opérateur pour `lock` l’utilisation dans une expression conditionnelle.

```cpp
operator bool();
```

### <a name="return-value"></a>Valeur retournée

`true`si une serrure `false` est tenue, sinon.

### <a name="remarks"></a>Notes

Cet opérateur se `_detail_class::_safe_bool` convertit en `bool` fait à ce qui est plus sûr que parce qu’il ne peut pas être converti en un type intégral.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads.  La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours. L’application principale attend de sortir jusqu’à ce que tous les threads de travailleur ont terminé leurs tâches.

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

## <a name="lockrelease"></a><a name="release"></a>serrure::libération

Libère une serrure.

```cpp
void release();
```

### <a name="remarks"></a>Notes

Si aucun verrou n’est tenu, `release` ne fait rien.

Vous n’avez pas à appeler cette fonction explicitement. Quand `lock` un objet sort de portée, `release`son destructeur appelle .

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads. La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours. L’application principale attend alors de sortir jusqu’à ce que tous les fils de travailleur aient terminé leurs tâches.

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

## <a name="locktry_acquire"></a><a name="try-acquire"></a>serrure::try_acquire

Acquiert un verrou sur un objet, en attente `bool` d’un temps spécifié et en retournant un pour signaler le succès de l’acquisition au lieu de jeter une exception.

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
Valeur de temps en millisecondes ou en tant que <xref:System.TimeSpan>.

### <a name="return-value"></a>Valeur retournée

`true`si le verrou `false` a été acquis, sinon.

### <a name="remarks"></a>Notes

Si un verrou a déjà été acquis, cette fonction ne fait rien.

### <a name="example"></a>Exemple

Cet exemple utilise une seule instance d’une classe à travers plusieurs threads. La classe utilise un verrou sur lui-même pour s’assurer que les accès à ses données internes sont cohérents pour chaque thread. Le fil d’application principal utilise un verrou sur le même cas de la classe pour vérifier périodiquement si des threads de travailleur existent toujours. L’application principale attend alors de sortir jusqu’à ce que tous les fils de travailleur aient terminé leurs tâches.

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

## <a name="lockoperator"></a><a name="operator-equality"></a>serrure: :opérateur

Opérateur d’égalité.

```cpp
template<class T> bool operator==(
   T t
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
Objet dont l'égalité doit être comparée.

### <a name="return-value"></a>Valeur retournée

Retourne `true` `t` si est le même que `false` l’objet de la serrure, sinon.

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

## <a name="lockoperator"></a><a name="operator-inequality"></a>serrure::opérateur!

Opérateur d’inégalité.

```cpp
template<class T> bool operator!=(
   T t
);
```

### <a name="parameters"></a>Paramètres

*T*<br/>
L’objectif de comparer pour l’inégalité.

### <a name="return-value"></a>Valeur retournée

Retourne `true` `t` si diffère de l’objet `false` de la serrure, sinon.

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
