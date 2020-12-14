---
description: 'En savoir plus sur : différences dans le comportement de gestion des exceptions sous/CLR'
title: Différences dans le comportement de gestion des exceptions sous-CLR
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: e7e07778e894448fea3d29acb3a32d71884be57c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252192"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Différences du comportement de gestion des exceptions dans /CLR

Les [concepts de base de l’utilisation des exceptions managées](../dotnet/basic-concepts-in-using-managed-exceptions.md) traitent de la gestion des exceptions dans les applications managées. Dans cette rubrique, les différences par rapport au comportement standard de la gestion des exceptions et certaines restrictions sont décrites en détail. Pour plus d’informations, consultez [la fonction _set_se_translator](../c-runtime-library/reference/set-se-translator.md).

## <a name="jumping-out-of-a-finally-block"></a><a name="vcconjumpingoutofafinallyblock"></a> Sortie d’un bloc finally

Dans le code C/C++ natif, le saut hors d’un bloc _ _ **finally** à l’aide de la gestion structurée des exceptions (SEH) est autorisé bien qu’il génère un avertissement.  Sous [/CLR](../build/reference/clr-common-language-runtime-compilation.md), le saut hors d’un bloc **finally** génère une erreur :

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

## <a name="raising-exceptions-within-an-exception-filter"></a><a name="vcconraisingexceptionswithinanexceptionfilter"></a> Déclenchement d’exceptions dans un filtre d’exception

Quand une exception est levée pendant le traitement d’un [filtre d’exception](../cpp/writing-an-exception-filter.md) dans du code managé, l’exception est interceptée et traitée comme si le filtre retourne 0.

Contrairement au comportement en code natif où une exception imbriquée est levée, le champ **ExceptionRecord** de la structure **EXCEPTION_RECORD** (telle que retournée par [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation)) est défini et le champ **ExceptionFlags** définit le bit 0x10. L’exemple suivant illustre cette différence de comportement :

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

## <a name="disassociated-rethrows"></a><a name="vccondisassociatedrethrows"></a> Réexceptions dissociées

**/CLR** ne prend pas en charge la levée à nouveau d’une exception en dehors d’un gestionnaire catch (appelée régénération dissociée). Les exceptions de ce type sont traitées comme une nouvelle levée C++ standard. Si une nouvelle levée dissociée est détectée lorsqu’il existe une exception managée active, l’exception est encapsulée en tant qu’exception C++, puis levée de nouveau. Les exceptions de ce type ne peuvent être interceptées qu’en tant qu’exception de type <xref:System.Runtime.InteropServices.SEHException> .

L’exemple suivant illustre une exception managée levée à nouveau en tant qu’exception C++ :

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

## <a name="exception-filters-and-exception_continue_execution"></a><a name="vcconexceptionfiltersandexception_continue_execution"></a> Filtres et EXCEPTION_CONTINUE_EXECUTION d’exception

Si un filtre retourne `EXCEPTION_CONTINUE_EXECUTION` dans une application managée, il est traité comme si le filtre avait été retourné `EXCEPTION_CONTINUE_SEARCH` . Pour plus d’informations sur ces constantes, consultez [instruction try-except](../cpp/try-except-statement.md).

L’exemple suivant illustre cette différence :

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

## <a name="the-_set_se_translator-function"></a><a name="vcconthe_set_se_translatorfunction"></a> Fonction _set_se_translator

La fonction de traduction, définie par un appel à `_set_se_translator` , affecte uniquement les captures dans le code non managé. L’exemple suivant illustre cette limitation :

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
[Gestion des exceptions dans MSVC](../cpp/exception-handling-in-visual-cpp.md)
