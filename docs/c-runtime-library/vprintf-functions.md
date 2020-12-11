---
description: 'En savoir plus sur les fonctions suivantes : vprintf'
title: Fonctions vprintf
ms.date: 11/04/2016
api_location:
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- vprintf
helpviewer_keywords:
- vprintf function
- formatted text [C++]
ms.assetid: 02ac7c51-eab1-4bf0-bf4c-77065e3fa744
ms.openlocfilehash: 54490518fd083826108da6a87e4a759fc2aa6227
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162071"
---
# <a name="vprintf-functions"></a>Fonctions vprintf

Chacune de ces fonctions `vprintf` prend un pointeur désignant une liste d’arguments, puis met en forme et écrit les données fournies dans une destination particulière. Les fonctions diffèrent dans la validation des paramètres effectuée, l’utilisation de chaînes à caractères larges ou sur un octet, la destination de sortie et la prise en charge de la spécification de l’ordre dans lequel les paramètres sont utilisés dans la chaîne de format.

[_vcprintf, _vcwprintf](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)\
[vfprintf, vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)\
[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)\
[vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)\
[vprintf, vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)\
[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)\
[vprintf_s, _vprintf_s_l, vwprintf_s, _vwprintf_s_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)\
[_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)\
[_vsnprintf, _vsnwprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 
 [vsprintf, vswprintf](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)\
[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)\
[vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)

## <a name="remarks"></a>Notes

Les fonctions `vprintf` sont semblables à leurs fonctions équivalentes, comme indiqué dans le tableau suivant. Toutefois, chaque fonction `vprintf` accepte un pointeur vers une liste d’arguments, alors que chacune de ces fonctions équivalentes accepte une liste d’arguments.

Ces fonctions mettent en forme les données pour la sortie vers les destinations, comme suit.

|Fonction|Fonction équivalente|Destination de sortie|Validation des paramètres|Prise en charge des paramètres positionnels|
|--------------|--------------------------|------------------------|--------------------------|----------------------------------|
|`_vcprintf`|[_cprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|console|Rechercher la valeur null.|non|
|`_vcwprintf`|[_cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|console|Rechercher la valeur null.|non|
|`vfprintf`|[fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*STREAM*|Rechercher la valeur null.|non|
|**vfprintf_p**|[fprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*STREAM*|Rechercher valeur null et format valide.|Oui|
|`vfprintf_s`|[fprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*STREAM*|Rechercher valeur null et format valide.|non|
|`vfwprintf`|[fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|*STREAM*|Rechercher la valeur null.|non|
|**vfwprintf_p**|[fwprintf_p](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|*STREAM*|Rechercher valeur null et format valide.|Oui|
|`vfwprintf_s`|[fwprintf_s](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|*STREAM*|Rechercher valeur null et format valide.|non|
|`vprintf`|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Rechercher la valeur null.|non|
|**vprintf_p**|[printf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Rechercher valeur null et format valide.|Oui|
|`vprintf_s`|[printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Rechercher valeur null et format valide.|non|
|`vwprintf`|[wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|`Stdout`|Rechercher la valeur null.|non|
|**vwprintf_p**|[wprintf_p](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|`Stdout`|Rechercher valeur null et format valide.|Oui|
|`vwprintf_s`|[wprintf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|`Stdout`|Rechercher valeur null et format valide.|non|
|**vsprintf**|[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher la valeur null.|non|
|**vsprintf_p**|[sprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher valeur null et format valide.|Oui|
|`vsprintf_s`|[sprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher valeur null et format valide.|non|
|`vswprintf`|[swprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher la valeur null.|non|
|**vswprintf_p**|[swprintf_p](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher valeur null et format valide.|Oui|
|`vswprintf_s`|[swprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher valeur null et format valide.|non|
|`_vscprintf`|[_vscprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher la valeur null.|non|
|`_vscwprintf`|[_vscwprintf](../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher la valeur null.|non|
|`_vsnprintf`|[_snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher la valeur null.|non|
|`_vsnwprintf`|[_snwprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|mémoire vers laquelle pointe la *mémoire tampon*|Rechercher la valeur null.|non|

L’argument `argptr` est de type `va_list`, qui est défini dans les VARARGS.H et STDARG.H. La variable `argptr` doit être initialisée par **va_start** et peut être réinitialisée par les appels ultérieurs à `va_arg` ; `argptr` pointe ensuite vers le début d’une liste d’arguments qui sont convertis et transmis pour la sortie en fonction des spécifications correspondantes dans l’argument *format*. *format* a la même forme et la même fonction que l’argument *format* pour [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Aucune de ces fonctions n’appelle `va_end`. Pour obtenir une description plus complète de chaque fonction `vprintf`, consultez la description de sa fonction équivalente, comme dans le tableau précédent.

`_vsnprintf` diffère de **vsprintf** en cela qu’il n’écrit pas plus de *count* octets dans la *mémoire tampon*.

Les versions de ces fonctions avec la valeur infix **w** dans leur nom sont des versions à caractères larges des fonctions correspondantes sans valeur infix **w** ; dans chacune de ces fonctions à caractères larges, *buffer* et *format* sont des chaînes à caractères larges. Dans le cas contraire, chaque fonction à caractères larges a un comportement identique à sa fonction SBCS équivalente.

Les versions de ces fonctions avec les suffixes **_s** et **_p** sont les versions les plus sécurisées. Ces versions valident les chaînes de format et génèrent une exception si la chaîne de format n’est pas bien formée (par exemple, si des caractères de formatage non valides sont utilisés).

Les versions de ces fonctions avec le suffixe **_p** permettent de spécifier l’ordre dans lequel les arguments fournis sont substitués dans la chaîne de format. Pour plus d’informations, consultez [Paramètres positionnels printf_p](../c-runtime-library/printf-p-positional-parameters.md).

Pour **vsprintf**, `vswprintf` `_vsnprintf` et `_vsnwprintf` , si la copie se produit entre des chaînes qui se chevauchent, le comportement n’est pas défini.

> [!IMPORTANT]
> Assurez-vous que *format* n'est pas une chaîne définie par l'utilisateur. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns). Si vous utilisez les versions sécurisées de ces fonctions (avec le suffixe **_s** ou **_p**), une chaîne de format de fournie par l’utilisateur risque de déclencher une exception de paramètre non valide si la chaîne fournie par l’utilisateur contient des caractères de mise en forme non valides.

## <a name="see-also"></a>Voir aussi

[E/S de flux](../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)
