---
description: 'En savoir plus sur : vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l'
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 27c91d6064b4a92da8a6f09e7d7e5b6bfb8bf95f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342151"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

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

*mémoire tampon*<br/>
Emplacement de stockage pour la sortie.

*sizeOfBuffer*<br/>
Taille de la *mémoire tampon* pour la sortie, en tant que nombre de caractères.

*count*<br/>
Nombre maximal de caractères à écrire (à l’exclusion du caractère null de fin) ou [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Spécification de format.

*argptr*<br/>
Pointeur vers la liste d'arguments.

*locale*<br/>
Paramètres régionaux à utiliser.

Pour plus d’informations, consultez [Spécifications de format](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valeur renvoyée

**vsnprintf_s**, **_vsnprintf_s** et **_vsnwprintf_s** retournent le nombre de caractères écrits, sans le caractère null de fin, ou une valeur négative si la troncation des données ou une erreur de sortie se produit.

* Si *Count* est inférieur à *sizeOfBuffer* et que le nombre de caractères de données est inférieur ou égal à *count*, ou *Count* est [_TRUNCATE](../../c-runtime-library/truncate.md) et que le nombre de caractères de données est inférieur à *sizeOfBuffer*, toutes les données sont écrites et le nombre de caractères est retourné.

* Si le *nombre* est inférieur à *sizeOfBuffer* , mais que les données dépassent le *nombre* *de caractères, les premiers caractères* sont écrits. La troncation des données restantes se produit et-1 est retourné sans appeler le gestionnaire de paramètre non valide.

* Si le nombre est [_TRUNCATE](../../c-runtime-library/truncate.md) et que le nombre de caractères de *données est supérieur* ou égal à *sizeOfBuffer*, la plus grande partie de la chaîne qui tient dans la *mémoire tampon* (avec une valeur null de fin) est écrite. La troncation des données restantes se produit et-1 est retourné sans appeler le gestionnaire de paramètre non valide.

* Si *Count* est égal à ou dépasse *sizeOfBuffer* mais que le nombre de caractères de données est inférieur à *sizeOfBuffer*, toutes les données sont écrites (avec une valeur null de fin) et le nombre de caractères est retourné.

* Si *le nombre et* le nombre de caractères des données sont égaux ou supérieurs à *sizeOfBuffer*, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution se poursuit après le gestionnaire de paramètres non valides, ces fonctions définissent la *mémoire tampon* sur une chaîne vide, attribuent à **errno** la valeur **ERANGE** et retournent-1.

* Si la *mémoire tampon* ou le *format* est un pointeur **null** , ou si *Count* est inférieur ou égal à zéro, le gestionnaire de paramètre non valide est appelé. Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent-1.

### <a name="error-conditions"></a>Conditions d'erreur

|**Condition**|Renvoie|**errno**|
|-----------------|------------|-------------|
|la *mémoire tampon* est **null**|-1|**EINVAL**|
|le *format* est **null**|-1|**EINVAL**|
|*nombre* <= 0|-1|**EINVAL**|
|*sizeOfBuffer* trop petit (et *count* ! = **_TRUNCATE**)|-1 (et la *mémoire tampon* est définie sur une chaîne vide)|**ERANGE**|

## <a name="remarks"></a>Notes

**vsnprintf_s** est identique à **_vsnprintf_s**. **vsnprintf_s** est inclus pour la conformité à la norme ANSI. **_vnsprintf** est conservé pour la compatibilité descendante.

Chacune de ces fonctions prend un pointeur vers une liste d’arguments, puis met en forme et écrit jusqu’à *compter* les caractères des données spécifiées dans la mémoire vers laquelle pointe la *mémoire tampon* et ajoute une valeur null de fin.

Si le *nombre* est [_TRUNCATE](../../c-runtime-library/truncate.md), ces fonctions écrivent autant de chaînes que possible dans la *mémoire tampon* tout en laissant de l’espace pour une valeur null de fin. Si la chaîne entière (avec une valeur null de fin) s’ajuste à la *mémoire tampon*, ces fonctions retournent le nombre de caractères écrits (à l’exclusion de la valeur null de fin); Sinon, ces fonctions retournent-1 pour indiquer que la troncation s’est produite.

Les versions de ces fonctions avec le suffixe **_L** sont identiques, sauf qu’elles utilisent les paramètres régionaux passés au lieu des paramètres régionaux du thread actuel.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Pour vous assurer qu’il y a de l’espace pour la valeur null de fin, assurez-vous que le *nombre* est strictement inférieur à la longueur de la mémoire tampon, ou utilisez **_TRUNCATE**.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-têtes facultatifs|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h> et \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h> ou \<wchar.h> , et \<stdarg.h>|\<varargs.h>*|

\* Requis pour la compatibilité UNIX V.

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
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
