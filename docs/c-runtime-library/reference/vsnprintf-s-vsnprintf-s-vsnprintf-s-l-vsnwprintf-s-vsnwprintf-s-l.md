---
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
apiname:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: 255c3b760dec1495a4f9a82915878a5504844f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188724"
---
# <a name="vsnprintfs-vsnprintfs-vsnprintfsl-vsnwprintfs-vsnwprintfsl"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Écrivez la sortie mise en forme en utilisant un pointeur désignant une liste d’arguments. Ces versions de [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage pour la sortie.

*sizeOfBuffer*<br/>
La taille de la *tampon* pour la sortie, comme le nombre de caractères.

*count*<br/>
Nombre maximal de caractères à écrire (à l’exclusion du caractère null de fin) ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Spécification de format.

*argptr*<br/>
Pointeur vers la liste d'arguments.

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d'informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur de retour

**vsnprintf_s**, **_vsnprintf_s** et **_vsnwprintf_s** retourner le nombre de caractères écrits, sans le caractère null de fin, ou une valeur négative si une erreur de sortie se produit. **vsnprintf_s** est identique à **_vsnprintf_s**. **vsnprintf_s** est inclus pour la conformité à la norme ANSI. **_vnsprintf** est conservé pour la compatibilité descendante.

Si le stockage requis pour stocker les données et un caractère null de fin dépasse *sizeOfBuffer*, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md), sauf si *nombre*  est [_TRUNCATE](../../c-runtime-library/truncate.md), auquel cas autant de caractères de la chaîne comme tiendront dans *tampon* est écrit et -1 retournée. Si l’exécution se poursuit après le Gestionnaire de paramètre non valide, ces fonctions définissent *tampon* sur une chaîne vide, définissez **errno** à **ERANGE**et retournent -1.

Si *tampon* ou *format* est un **NULL** pointeur, ou si *nombre* est inférieure ou égale à zéro, le Gestionnaire de paramètre non valide est appelé. Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retournent -1.

### <a name="error-conditions"></a>Conditions d’erreur

|**Condition**|Retourner|**errno**|
|-----------------|------------|-------------|
|*mémoire tampon* est **NULL**|-1|**EINVAL**|
|*format* est **NULL**|-1|**EINVAL**|
|*count* <= 0|-1|**EINVAL**|
|*sizeOfBuffer* trop petit (et *nombre* ! = **_TRUNCATE**)|-1 (et *tampon* définie sur une chaîne vide)|**ERANGE**|

## <a name="remarks"></a>Notes

Chacune de ces fonctions prend un pointeur désignant une liste d’arguments, puis met en forme et écrit jusqu'à *nombre* caractères des données fournies à la mémoire vers laquelle pointe *tampon* et ajoute un caractère null de fin.

Si *nombre* est [_TRUNCATE](../../c-runtime-library/truncate.md), ces fonctions écrivent autant de caractères de la chaîne qui tient *tampon* tout en laissant de l’espace pour un caractère null. Si la chaîne entière (avec le caractère null de fin) s’intègre *tampon*, puis ces fonctions retournent le nombre de caractères écrits (sans compter le caractère null de fin) ; sinon, ces fonctions retournent -1 pour indiquer que la troncation s’est produite.

Les versions de ces fonctions avec le **_l** suffixe sont identiques, sauf qu’ils utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/desktop/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Pour vous assurer qu’il y place pour le caractère null, veillez à ce que *nombre* est strictement inférieur à la longueur de la mémoire tampon ou utilisez **_TRUNCATE**.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h> ou \<wchar.h> et \<stdarg.h>|\<varargs.h>*|

\** Nécessaire pour la compatibilité avec UNIX V.

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf, fonctions](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
