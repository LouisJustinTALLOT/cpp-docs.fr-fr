---
title: Différences du comportement de gestion des exceptions dans -CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: 940d297ff77248ba9e9980f7032b5d722d95c7eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364373"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Différences du comportement de gestion des exceptions dans /CLR

[Basic Concepts in Using Managed Exceptions](../dotnet/basic-concepts-in-using-managed-exceptions.md) discute du traitement des exceptions dans les applications gérées. Dans ce sujet, les différences par rapport au comportement standard de la gestion des exceptions et certaines restrictions sont discutées en détail. Pour plus d’informations, voir [The _set_se_translator Function](../c-runtime-library/reference/set-se-translator.md).

## <a name="jumping-out-of-a-finally-block"></a><a name="vcconjumpingoutofafinallyblock"></a>Sauter d’un bloc enfin

Dans le code C/CMd natif, il est permis de sauter d’un**bloc** à l’aide d’une manipulation d’exception structurée (SEH) bien qu’il produise un avertissement.  Sous [/clr](../build/reference/clr-common-language-runtime-compilation.md), sauter d’un bloc **enfin** provoque une erreur:

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

## <a name="raising-exceptions-within-an-exception-filter"></a><a name="vcconraisingexceptionswithinanexceptionfilter"></a>Augmenter les exceptions dans un filtre d’exception

Lorsqu’une exception est soulevée lors du traitement d’un [filtre d’exception](../cpp/writing-an-exception-filter.md) dans le code géré, l’exception est prise et traitée comme si le filtre relege 0.

Ceci contraste avec le comportement dans le code indigène où une exception imbriquée est soulevée, le champ **ExceptionRecord** dans la structure **EXCEPTION_RECORD** (tel que retourné par [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)) est fixé, et le champ **ExceptionFlags** définit le bit 0x10. L’exemple suivant illustre cette différence de comportement :

```cpp
// clr_exception_handling_5.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

#ifndef false
#define false 0
#endif

int *p;

int filter(PEXCEPTION_POINTERS ExceptionPointers) {
   PEXCEPTION_RECORD ExceptionRecord =
                     ExceptionPointers->ExceptionRecord;

   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {
      // not a nested exception, throw one
      *p = 0; // throw another AV
   }
   else {
      printf("Caught a nested exception\n");
      return 1;
    }

   assert(false);

   return 0;
}

void f(void) {
   __try {
      *p = 0;   // throw an AV
   }
   __except(filter(GetExceptionInformation())) {
      printf_s("We should execute this handler if "
                 "compiled to native\n");
    }
}

int main() {
   __try {
      f();
   }
   __except(1) {
      printf_s("The handler in main caught the "
               "exception\n");
    }
}
```

### <a name="output"></a>Output

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

## <a name="disassociated-rethrows"></a><a name="vccondisassociatedrethrows"></a>Rethrows dissociés

**/clr** n’appuie pas la ressociation d’une exception à l’extérieur d’un gestionnaire de capture (connu sous le nom de rethrow dissocié). Les exceptions de ce type sont traitées comme un rethrow standard de C. Si une recroissance dissociée est rencontrée lorsqu’il y a une exception gérée active, l’exception est enveloppée comme une exception CD, puis ressoinée. Les exceptions de ce type ne peuvent <xref:System.Runtime.InteropServices.SEHException>être prises qu’à l’exception du type .

L’exemple suivant démontre une exception gérée rethrown comme une exception C ' :

```cpp
// clr_exception_handling_6.cpp
// compile with: /clr
using namespace System;
#include <assert.h>
#include <stdio.h>

void rethrow( void ) {
   // This rethrow is a dissasociated rethrow.
   // The exception would be masked as SEHException.
   throw;
}

int main() {
   try {
      try {
         throw gcnew ApplicationException;
      }
      catch ( ApplicationException^ ) {
         rethrow();
         // If the call to rethrow() is replaced with
         // a throw statement within the catch handler,
         // the rethrow would be a managed rethrow and
         // the exception type would remain
         // System::ApplicationException
      }
   }

    catch ( ApplicationException^ ) {
      assert( false );

      // This will not be executed since the exception
      // will be masked as SEHException.
    }
   catch ( Runtime::InteropServices::SEHException^ ) {
      printf_s("caught an SEH Exception\n" );
    }
}
```

### <a name="output"></a>Output

```Output
caught an SEH Exception
```

## <a name="exception-filters-and-exception_continue_execution"></a><a name="vcconexceptionfiltersandexception_continue_execution"></a>Filtres d’exception et EXCEPTION_CONTINUE_EXECUTION

Si un `EXCEPTION_CONTINUE_EXECUTION` filtre revient dans une application gérée, `EXCEPTION_CONTINUE_SEARCH`il est traité comme si le filtre était retourné. Pour plus d’informations sur ces constantes, voir [try-except Statement](../cpp/try-except-statement.md).

L’exemple suivant démontre cette différence :

```cpp
// clr_exception_handling_7.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

int main() {
   int Counter = 0;
   __try {
      __try  {
         Counter -= 1;
         RaiseException (0xe0000000|'seh',
                         0, 0, 0);
         Counter -= 2;
      }
      __except (Counter) {
         // Counter is negative,
         // indicating "CONTINUE EXECUTE"
         Counter -= 1;
      }
    }
    __except(1) {
      Counter -= 100;
   }

   printf_s("Counter=%d\n", Counter);
}
```

### <a name="output"></a>Output

```Output
Counter=-3
```

## <a name="the-_set_se_translator-function"></a><a name="vcconthe_set_se_translatorfunction"></a>La fonction _set_se_translator

La fonction de traducteur, `_set_se_translator`définie par un appel à , n’affecte que les captures dans le code non menté. L’exemple suivant démontre cette limitation :

```cpp
// clr_exception_handling_8.cpp
// compile with: /clr /EHa
#include <iostream>
#include <windows.h>
#include <eh.h>
#pragma warning (disable: 4101)
using namespace std;
using namespace System;

#define MYEXCEPTION_CODE 0xe0000101

class CMyException {
public:
   unsigned int m_ErrorCode;
   EXCEPTION_POINTERS * m_pExp;

   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}

   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )
         : m_ErrorCode( i ), m_pExp( pExp ) {}

   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),
                                      m_pExp( c.m_pExp ) {}

   friend ostream& operator <<
                 ( ostream& out, const CMyException& inst ) {
      return out <<  "CMyException[\n" <<
             "Error Code: " << inst.m_ErrorCode <<  "]";
    }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {
   cout <<  "In my_trans_func.\n";
   throw CMyException( u, pExp );
}

#pragma managed
void managed_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );
   }
   catch ( CMyException x ) {}
   catch ( ... ) {
      printf_s("This is invoked since "
               "_set_se_translator is not "
               "supported when /clr is used\n" );
    }
}

#pragma unmanaged
void unmanaged_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE,
                      0, 0, 0 );
   }
   catch ( CMyException x ) {
      printf("Caught an SEH exception with "
             "exception code: %x\n", x.m_ErrorCode );
    }
    catch ( ... ) {}
}

// #pragma managed
int main( int argc, char ** argv ) {
   _set_se_translator( my_trans_func );

   // It does not matter whether the translator function
   // is registered in managed or unmanaged code
   managed_func();
   unmanaged_func();
}
```

### <a name="output"></a>Output

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Manipulation d’exception en MSVC](../cpp/exception-handling-in-visual-cpp.md)
