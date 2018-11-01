---
title: Mappages de texte générique dans Tchar.h
ms.date: 11/04/2016
f1_keywords:
- tchar.h
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: 969894502689dd5aeeeaa27404bafc3c483c1336
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667582"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mappages de texte générique dans Tchar.h

Pour simplifier le transport de code pour une utilisation internationale, la bibliothèque Runtime Microsoft fournit des mappages de texte générique spécifiques à Microsoft pour nombreux types de données, routines et autres objets. Vous pouvez utiliser ces mappages, qui sont définis dans Tchar.h, pour écrire du code générique qui peut être compilé sur un octet, multioctet, ou de caractère Unicode définit, en fonction d’une constante de manifeste que vous définissez à l’aide un `#define` instruction. Les mappages de texte générique sont des extensions Microsoft non compatibles ANSI.

En utilisant le fichier Tchar.h, vous pouvez générer un octet, jeu de caractères multioctets (MBCS) et les applications Unicode à partir des mêmes sources. Tchar.h définit des macros (qui ont le préfixe `_tcs`) qui, avec les définitions de préprocesseur, correspondent aux `str`, `_mbs`, ou `wcs` fonctions, comme il convient. Pour générer du MBCS, définissez le symbole `_MBCS`. Pour générer du Unicode, définissez le symbole `_UNICODE`. Pour générer une application d’un octet, définissez ni (la valeur par défaut). Par défaut, `_MBCS` est défini pour les applications MFC.

Le `_TCHAR` type de données est défini de façon conditionnelle dans Tchar.h. Si le symbole `_UNICODE` est défini pour votre build, `_TCHAR` est défini comme **wchar_t**; sinon, pour un octet et MBCS builds, il est défini comme **char**. (**wchar_t**, type de données à caractère élargi Unicode de base, est l’équivalent de 16 bits de 8 bits signé **char**.) Dans les applications internationales, utilisez le `_tcs` famille de fonctions qui opèrent dans `_TCHAR` unités, non en octets. Par exemple, `_tcsncpy` copies `n` `_TCHARs`, et non `n` octets.

Étant donné que les fonctions de certains gestion de chaîne unique le définir de caractère octet (SBCS) (signé) `char*` paramètres, des résultats d’avertissement du compilateur une incompatibilité type lorsque `_MBCS` est défini. Il existe trois façons d’éviter cet avertissement :

1. Utilisez les thunks de la fonction inline de type sécurisé dans Tchar.h. Il s'agit du comportement par défaut.

1. Utilisez les macros directes dans Tchar.h en définissant `_MB_MAP_DIRECT` sur la ligne de commande. Ce faisant, vous devez associer manuellement les types. La méthode est plus rapide, ce n’est pas de type sécurisé.

1. Utilisez les thunks de fonction de bibliothèque liée statiquement de type sécurisé dans Tchar.h. Pour cela, définissez la constante `_NO_INLINING` sur la ligne de commande. Cette méthode est la plus lente, mais la plus sécurisée pour le type.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directives de préprocesseur pour les mappages de texte générique

|# define|Version compilée|Exemple|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (caractères larges)|`_tcsrev` correspond à `_wcsrev`|
|`_MBCS`|Caractères multioctets|`_tcsrev` correspond à `_mbsrev`|
|Aucun (la valeur par défaut ne possède aucun `_UNICODE` ni `_MBCS` défini)|SBCS (ASCII)|`_tcsrev` correspond à `strrev`|

Par exemple, la fonction de texte générique `_tcsrev`, qui est défini dans Tchar.h, correspond à `_mbsrev` si vous avez défini `_MBCS` dans votre programme, ou à `_wcsrev` si vous avez défini `_UNICODE`. Sinon, `_tcsrev` est mappée à `strrev`. Autres mappages de type de données sont fournis dans Tchar.h pour faciliter la programmation, mais `_TCHAR` est le plus utile.

### <a name="generic-text-data-type-mappings"></a>Mappages de types de données de texte générique

|Texte générique<br /> Nom de Type de données|_UNICODE &AMP;<br /> _MBCS non définis|_MBCS<br /> Défini|_UNICODE<br /> Défini|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**char signé**|**char signé**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` ou `_TEXT`|Aucun effet (supprimé par le préprocesseur)|Aucun effet (supprimé par le préprocesseur)|`L` (convertit le caractère ou la chaîne suivante en son équivalent Unicode)|

Pour obtenir la liste des mappages de texte générique des routines, variables et autres objets, consultez [mappages de texte générique](../c-runtime-library/generic-text-mappings.md) dans le Run-Time Library Reference.

> [!NOTE]
>  N’utilisez pas le `str` famille de fonctions avec des chaînes Unicode, qui sont susceptibles de contenir des octets null incorporés. De même, n’utilisez pas le `wcs` famille de fonctions avec des chaînes MBCS (ou SBCS).

Les fragments de code suivants illustrent l’utilisation de `_TCHAR` et `_tcsrev` pour le mappage sur les modèles MBCS, Unicode et SBCS.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Si `_MBCS` a été défini, le préprocesseur mappe ce fragment à ce code :

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Si `_UNICODE` a été défini, le préprocesseur mappe ce fragment à ce code :

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Si ni `_MBCS` ni `_UNICODE` ont été défini, le préprocesseur mappe le fragment de code de ASCII codés sur un octet, comme suit :

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Par conséquent, vous pouvez écrire, maintenir et compiler un fichier de code source unique à exécuter avec des routines qui sont spécifiques à un des trois types de jeux de caractères.

## <a name="see-also"></a>Voir aussi

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
[Utilisation de types de données TCHAR.H avec _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)