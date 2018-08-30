---
title: snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _snwprintf
- _snprintf
- _snprintf_l
- _snwprintf_l
- snprintf
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
- ntoskrnl.exe
apitype: DLLExport
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe100cbd38581b733c07b5d129d215f368e27aa7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203516"
---
# <a name="snprintf-snprintf-snprintfl-snwprintf-snwprintfl"></a>snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l
Écrit des données mises en forme dans une chaîne. Il existe des versions plus sécurisées de ces fonctions. Consultez [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

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

*buffer*<br/>
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

Laisser **len** être la longueur de la chaîne de données mises en forme, non compris le caractère null de fin. Les deux **len** et *nombre* sont exprimées en octets pour **snprintf** et **_snprintf**, caractères larges pour **_snwprintf**.

Pour toutes les fonctions, si **len** < *nombre*, **len** caractères sont stockés dans *tampon*, une marque de fin null est ajoutée, et **len** est retourné.

Le **snprintf** fonction tronque le résultat lorsque **len** est supérieur ou égal à *nombre*, en plaçant une marque de fin null à `buffer[count-1]`. La valeur retournée est **len**, le nombre de caractères qui aurait été sortie si *nombre* était suffisante. Le **snprintf** fonction retourne une valeur négative si une erreur de codage se produit.

Pour toutes les fonctions autres que **snprintf**si **len** = *nombre*, **len** caractères sont stockés dans  *mémoire tampon*, aucune marque de fin null n’est ajoutée, et **len** est retourné. Si **len** > *nombre*, *nombre* caractères sont stockés dans *tampon*, aucune marque de fin null n’est ajoutée et qu’une valeur négative valeur est retournée.

Si *tampon* est un pointeur null et *nombre* est égal à zéro, **len** est retourné en tant que le nombre de caractères requis pour mettre en forme la sortie, sans le caractère null de fin. Pour effectuer un appel réussi avec le même *argument* et *paramètres régionaux* paramètres, allouez une mémoire tampon contenant au moins **len** + 1 caractères.

Si *tampon* est un pointeur null et *nombre* est différent de zéro, ou si *format* est un pointeur null, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et la valeur **errno** à **EINVAL**.

Pour obtenir des informations sur ces codes d’erreur et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **snprintf** (fonction) et le **_snprintf** famille de fonctions forme et stockent *nombre* caractères au maximum dans *tampon*. Le **snprintf** fonction stocke toujours un caractère null de fin, tronque la sortie si nécessaire. Le **_snprintf** famille de fonctions ajoute uniquement un caractère null de fin si la longueur de la chaîne mise en forme est strictement inférieur à *nombre* caractères. Chaque *argument* (le cas échéant) est converti et sorti selon la spécification de format correspondante dans *format*. Le format se compose de caractères ordinaires et a les mêmes forme et fonction que le *format* argument pour [printf](printf-printf-l-wprintf-wprintf-l.md). Si une copie se produit entre des chaînes qui se chevauchent, le comportement est indéfini.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Étant donné que le **_snprintf** fonctions ne garantissent pas le caractère null de fin, en particulier, lorsque la valeur de retour est *nombre*— vous assurer qu’ils sont suivis par le code qui ajoute la marque de fin null. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/desktop/SecBP/avoiding-buffer-overruns).

Depuis le composant UCRT dans Visual Studio 2015 et Windows 10, **snprintf** n’est plus identique à **_snprintf**. Le **snprintf** comportement de la fonction est désormais conforme à la norme C99.

**_snwprintf** est une version à caractères larges de **_snprintf**; les arguments de pointeur à **_snwprintf** sont des chaînes à caractères larges. Détection d’erreurs dans d’encodage **_snwprintf** peut différer de celle dans **_snprintf**. **_snwprintf**, comme **swprintf**, écrit la sortie dans une chaîne au lieu d’une destination de type **fichier**.

Les versions de ces fonctions qui ont le **_l** suffixe sont identiques, sauf qu’ils utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntprintf**|**_snprintf**|**_snprintf**|**_snwprintf**|
|**_sntprintf_l**|**_snprintf_l**|**_snprintf_l**|**_snwprintf_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**snprintf**, **_snprintf**, **_snprintf_l**|\<stdio.h>|
|**_snwprintf**, **_snwprintf_l**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
