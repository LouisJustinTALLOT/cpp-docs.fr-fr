---
title: Différences de comportement dans - CLR de la gestion des exceptions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: df2f04e89175855db36790f22e8fd718288603b2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43217430"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>Différences du comportement de gestion des exceptions dans /CLR
[Concepts de base dans l’utilisation des Exceptions](../dotnet/basic-concepts-in-using-managed-exceptions.md) aborde la gestion des exceptions dans les applications managées. Dans cette rubrique, les différences du comportement standard de gestion des exceptions et certaines restrictions sont décrites en détail. Pour plus d’informations, consultez [la fonction _set_se_translator](../c-runtime-library/reference/set-se-translator.md).  
  
##  <a name="vcconjumpingoutofafinallyblock"></a> Saut hors d’un bloc Finally  
 Dans le code C/C++ natif, saut hors d’un __**enfin** bloc à l’aide de la gestion structurée des exceptions (SEH) est autorisée bien qu’il génère un avertissement.  Sous [/CLR](../build/reference/clr-common-language-runtime-compilation.md), saut hors un **enfin** bloc provoque une erreur :  
  
```  
// clr_exception_handling_4.cpp  
// compile with: /clr  
int main() {  
   try {}  
   finally {  
      return 0;   // also fails with goto, break, continue  
    }  
}   // C3276  
```  
  
##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a> Déclenchement d’Exceptions dans un filtre d’Exception  
 Lorsqu’une exception est levée pendant le traitement d’un [filtre d’exception](../cpp/writing-an-exception-filter.md) dans du code géré, l’exception est interceptée et traitée comme si le filtre retourne 0.  
  
 Ce comportement diffère du comportement en code natif où une exception imbriquée est déclenchée, le **ExceptionRecord** champ dans le **EXCEPTION_RECORD** structure (tel que retourné par [ GetExceptionInformation](/windows/desktop/Debug/getexceptioninformation)) est définie et le **ExceptionFlags** champ définit le bit 0 x 10. L’exemple suivant illustre cette différence de comportement :  
  
```  
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
  
### <a name="output"></a>Sortie  
  
```  
Caught a nested exception  
We should execute this handler if compiled to native  
```  
  
##  <a name="vccondisassociatedrethrows"></a> Levées dissociées  
 **/ CLR** ne prend pas en charge la nouvelle levée d’une exception en dehors d’un gestionnaire catch (appelée dissociée). Les exceptions de ce type sont traitées comme une rethrow C++ standard. Si dissociée se produite lorsqu’il existe une exception managée active, l’exception est encapsulée comme une exception C++ et puis levée de nouveau. Exceptions de ce type ne peuvent être interceptées en tant qu’exception de type [System::SEHException](https://msdn.microsoft.com/library/system.runtime.interopservices.sehexception.aspx).  
  
 L’exemple suivant montre une exception managée est levée de nouveau en tant qu’une exception C++ :  
  
```  
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
  
### <a name="output"></a>Sortie  
  
```  
caught an SEH Exception  
```  
  
##  <a name="vcconexceptionfiltersandexception_continue_execution"></a> Filtres d’exception et EXCEPTION_CONTINUE_EXECUTION  
 Si un filtre retourne `EXCEPTION_CONTINUE_EXECUTION` dans une application managée, il est traité comme si le filtre a renvoyé `EXCEPTION_CONTINUE_SEARCH`. Pour plus d’informations sur ces constantes, consultez [essayez-EXCEPT, instruction](../cpp/try-except-statement.md).  
  
 L’exemple suivant illustre cette différence :  
  
```  
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
  
### <a name="output"></a>Sortie  
  
```  
Counter=-3  
```  
  
##  <a name="vcconthe_set_se_translatorfunction"></a> La fonction _set_se_translator  
 La fonction de traduction, défini par un appel à `_set_se_translator`, affecte uniquement les captures en code non managé. L’exemple suivant illustre cette limitation :  
  
```  
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
  
### <a name="output"></a>Sortie  
  
```  
This is invoked since _set_se_translator is not supported when /clr is used  
In my_trans_func.  
Caught an SEH exception with exception code: e0000101  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)