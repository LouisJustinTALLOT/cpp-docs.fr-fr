---
title: snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l
description: Informations de référence sur l’API pour snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_, qui écrivent des données mises en forme dans une chaîne.
ms.date: 08/27/2020
api_name:
- _snwprintf
- _snprintf
- _snprintf_l
- _snwprintf_l
- snprintf
api_location:
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _snprintf
- snprintf_l
- snwprintf_l
- sntprintf
- snprintf
- _sntprintf
- _sntprintf_l
- sntprintf_l
- snwprintf
- _snprintf_l
- _snwprintf
- _snwprintf_l
helpviewer_keywords:
- snwprintf_l function
- sntprintf_l function
- snprintf_l function
- _snwprintf_l function
- _sntprintf_l function
- _snwprintf function
- _snprintf function
- _sntprintf function
- _snprintf_l function
- snwprintf function
- snprintf function
- sntprintf function
- formatted text [C++]
ms.assetid: 5976c9c8-876e-4ac9-a515-39f3f7fd0925
ms.openlocfilehash: b4d8865d5297afe3d48f2bb48cc85a0d10535dfd
ms.sourcegitcommit: c8f1605354724a13566bc3b0fac3c5d98265f1d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89062196"
---
# <a name="snprintf-_snprintf-_snprintf_l-_snwprintf-_snwprintf_l"></a>snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l

Écrit des données mises en forme dans une chaîne. Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf(
   char *buffer,
   size_t count,
   const char *format [,
   argument] ...
);
int _snprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
);
int _snwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format [,
   argument] ...
);
int _snwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
template <size_t size>
int _snprintf(
   char (&buffer)[size],
   size_t count,
   const char *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format [,
   argument] ...
); // C++ only
template <size_t size>
int _snwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale [,
   argument] ...
); // C++ only
```

### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Emplacement de stockage pour la sortie.

*count*<br/>
Nombre maximal de caractères à stocker.

*format*<br/>
Chaîne de contrôle de format.

*argument*<br/>
Arguments facultatifs.

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d’informations, consultez [Syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur de retour

Laissez **Len** la longueur de la chaîne de données mise en forme, à l’exclusion de la valeur null de fin. **Len** et **Count** sont tous deux le nombre de caractères pour **snprintf** et **_snprintf**, et le nombre de caractères larges pour **_snwprintf**.

Pour toutes les fonctions, si le nombre de **nbcars**  <  *count*, les caractères **Len** sont stockés dans la *mémoire tampon*, un terminateur null est ajouté et **Len** est retourné.

La fonction **snprintf** tronque la sortie quand **Len** est supérieur ou égal à *Count*, en plaçant une marque de fin null à `buffer[count-1]` . La valeur retournée est **Len**, le nombre de caractères qui auraient été générés si *Count* était suffisamment grand. La fonction **snprintf** retourne une valeur négative si une erreur d’encodage se produit.

Pour toutes les fonctions autres que **snprintf**, **si Len**  =  *Count*, les caractères **Len** sont stockés dans *buffer*, aucun terminateur NULL n’est ajouté, et **Len** est retourné. Si **len**  >  le*nombre*de nbcars, le *nombre* de caractères est stocké dans la *mémoire tampon*, aucun terminateur NULL n’est ajouté, et une valeur négative est retournée.

Si *buffer* est un pointeur null et que *Count* est égal à zéro, **Len** est retourné comme nombre de caractères requis pour mettre en forme la sortie, à l’exclusion de la valeur null de fin. Pour effectuer un appel réussi avec les mêmes paramètres d' *argument* et paramètres *régionaux* , allouez une mémoire tampon contenant au moins **Len** + 1 caractères.

Si la *mémoire tampon* est un pointeur null et que le *nombre* est différent de zéro, ou si le *format* est un pointeur null, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent-1 et attribuent à **errno** la valeur **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Remarques

La fonction **snprintf** et la famille **_snprintf** de fonctions formatent et stockent le *nombre* de caractères maximum dans la *mémoire tampon*. La fonction **snprintf** stocke toujours un caractère null de fin et tronque la sortie si nécessaire. La famille **_snprintf** des fonctions ajoute uniquement un caractère null de fin si la longueur de la chaîne mise en forme est strictement inférieure à *Count* caractères. Chaque *argument* (le cas échéant) est converti et est généré en fonction de la spécification de format correspondante au *format*. Le format se compose de caractères ordinaires et a la même forme et fonction que l’argument *format* pour [printf](printf-printf-l-wprintf-wprintf-l.md). Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Étant donné que les fonctions **_snprintf** ne garantissent pas la terminaison NULL, en particulier lorsque la valeur de retour est *Count*, assurez-vous qu’elles sont suivies du code qui ajoute la marque de fin null. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

À partir de UCRT dans Visual Studio 2015 et Windows 10, **snprintf** n’est plus identique à **_snprintf**. Le comportement de la fonction **snprintf** est désormais conforme à la norme C99.

**_snwprintf** est une version à caractères larges de **_snprintf**; les arguments de pointeur pour **_snwprintf** sont des chaînes à caractères larges. La détection des erreurs d’encodage dans **_snwprintf** peut différer de celle de **_snprintf**. **_snwprintf**, tout comme **swprintf**, écrit la sortie dans une chaîne au lieu d’une destination de type **file**.

Les versions de ces fonctions qui ont le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf**|**_snprintf**|**_snprintf**|**_snwprintf**|
|**_sntprintf_l**|**_snprintf_l**|**_snprintf_l**|**_snwprintf_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**snprintf**, **_snprintf**,  **_snprintf_l**|\<stdio.h>|
|**_snwprintf**, **_snwprintf_l**|\<stdio.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_snprintf.c
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

#if !defined(__cplusplus)
typedef int bool;
const bool true = 1;
const bool false = 0;
#endif

#define FAIL 0 // change to 1 and see what happens

int main(void)
{
   char buffer[200];
   const static char s[] = "computer"
#if FAIL
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
"computercomputercomputercomputercomputercomputercomputercomputer"
#endif
   ;
   const char c = 'l';
   const int i = 35;
#if FAIL
   const double fp = 1e300; // doesn't fit in the buffer
#else
   const double fp = 1.7320534;
#endif
   /* !subtract one to prevent "squeezing out" the terminal null! */
   const int bufferSize = sizeof(buffer)/sizeof(buffer[0]) - 1;
   int bufferUsed = 0;
   int bufferLeft = bufferSize - bufferUsed;
   bool bSuccess = true;
   buffer[0] = 0;

   /* Format and print various data: */

   if (bufferLeft > 0)
   {
      int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
      bufferLeft, "   String: %s\n", s ); // C4996
      // Note: _snprintf is deprecated; consider _snprintf_s instead
      if (bSuccess = (perElementBufferUsed >= 0))
      {
         bufferUsed += perElementBufferUsed;
         bufferLeft -= perElementBufferUsed;
         if (bufferLeft > 0)
         {
            int perElementBufferUsed = _snprintf(&buffer[bufferUsed],
            bufferLeft, "   Character: %c\n", c ); // C4996
            if (bSuccess = (perElementBufferUsed >= 0))
            {
               bufferUsed += perElementBufferUsed;
               bufferLeft -= perElementBufferUsed;
               if (bufferLeft > 0)
               {
                  int perElementBufferUsed = _snprintf(&buffer
                  [bufferUsed], bufferLeft, "   Integer: %d\n", i ); // C4996
                  if (bSuccess = (perElementBufferUsed >= 0))
                  {
                     bufferUsed += perElementBufferUsed;
                     bufferLeft -= perElementBufferUsed;
                     if (bufferLeft > 0)
                     {
                        int perElementBufferUsed = _snprintf(&buffer
                        [bufferUsed], bufferLeft, "   Real: %f\n", fp ); // C4996
                        if (bSuccess = (perElementBufferUsed >= 0))
                        {
                           bufferUsed += perElementBufferUsed;
                        }
                     }
                  }
               }
            }
         }
      }
   }

   if (!bSuccess)
   {
      printf("%s\n", "failure");
   }
   else
   {
      /* !store null because _snprintf doesn't necessarily (if the string
       * fits without the terminal null, but not with it)!
       * bufferUsed might be as large as bufferSize, which normally is
       * like going one element beyond a buffer, but in this case
       * subtracted one from bufferSize, so we're ok.
       */
      buffer[bufferUsed] = 0;
      printf( "Output:\n%s\ncharacter count = %d\n", buffer, bufferUsed );
   }
   return EXIT_SUCCESS;
}
```

```Output
Output:
   String: computer
   Character: l
   Integer: 35
   Real: 1.732053

character count = 69
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
