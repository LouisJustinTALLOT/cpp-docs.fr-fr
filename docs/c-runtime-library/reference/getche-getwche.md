---
title: _getche, _getwche | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _getwche
- _getche
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- getwche
- _getche
- _getwche
dev_langs:
- C++
helpviewer_keywords:
- characters, getting from console
- _getwche function
- getche function
- console, reading from
- getwche function
- _getche function
ms.assetid: eac978a8-c43a-4130-938f-54f12e2a0fda
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 050fa0024c827caf8a7f27b5462a341bea344bfb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2018
---
# <a name="getche-getwche"></a>_getche, _getwche
Obtient un caractère à partir de la console et l’affichent.  
  
> [!IMPORTANT]
>  Cette API ne peut pas être utilisée dans les applications qui s’exécutent dans le Windows Runtime. Pour plus d’informations, consultez [fonctions CRT non prises en charge dans les applications de plateforme Windows universelle](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _getche( void );  
wint_t _getwche( void );  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le caractère lu. Aucun retour d'erreur.  
  
## <a name="remarks"></a>Notes  
 Les fonctions `_getche` et `_getwche` lisent un caractère à partir de la console, avec affichage sur celle-ci. Aucune de ces fonctions ne peut être utilisée pour lire Ctrl+C. Pour la lecture d’une touche de fonction ou de direction, chaque fonction doit être appelée deux fois ; le premier appel retourne 0 ou 0xE0, tandis que le second retourne le code de la touche.  
  
 Ces fonctions verrouillent le thread appelant et sont donc thread-safe. Pour les versions sans verrouillage, consultez [_getche_nolock, _getwche_nolock](../../c-runtime-library/reference/getche-nolock-getwche-nolock.md).  
  
### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique  
  
|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_getche`|`_getche`|`_getch`|`_getwche`|  
  
## <a name="requirements"></a>Configuration requise  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_getche`|\<conio.h>|  
|`_getwche`|\<conio.h> ou \<wchar.h>|  
  
 Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemple  
  
```  
// crt_getche.c  
// compile with: /c  
// This program reads characters from  
// the keyboard until it receives a 'Y' or 'y'.  
  
#include <conio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
  
   _cputs( "Type 'Y' when finished typing keys: " );  
   do  
   {  
      ch = _getche();  
      ch = toupper( ch );  
   } while( ch != 'Y' );  
  
   _putch( ch );  
   _putch( '\r' );    // Carriage return  
   _putch( '\n' );    // Line feed       
}  
```  
  
```Input  
abcdefy
```
  
```Output  
Type 'Y' when finished typing keys: abcdefyY  
```  
  
## <a name="see-also"></a>Voir aussi  
 [E/S de console et de port](../../c-runtime-library/console-and-port-i-o.md)   
 [_cgets, _cgetws](../../c-runtime-library/cgets-cgetws.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [_ungetch, _ungetwch, _ungetch_nolock, _ungetwch_nolock](../../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)