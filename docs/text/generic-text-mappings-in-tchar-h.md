---
description: En savoir plus sur les mappages de Generic-Text dans Tchar. h
title: Mappages de Generic-Text dans Tchar. h
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: f083dc03eab7db25b54955d8d34a13f2b5b7197b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118346"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mappages de Generic-Text dans Tchar. h

Pour simplifier le transport de code pour une utilisation internationale, la bibliothèque Runtime Microsoft fournit des mappages de texte générique spécifiques à Microsoft pour de nombreux types de données, routines et autres objets. Vous pouvez utiliser ces mappages, qui sont définis dans Tchar. h, pour écrire du code générique qui peut être compilé pour les jeux de caractères codés sur un octet, multioctets ou Unicode, en fonction d’une constante de manifeste que vous définissez à l’aide d’une `#define` instruction. Les mappages de texte générique sont des extensions Microsoft non compatibles ANSI.

En utilisant Tchar. h, vous pouvez générer des applications codées sur un octet, un jeu de caractères multioctets (MBCS) et des applications Unicode à partir des mêmes sources. Tchar. h définit des macros (qui ont le préfixe `_tcs` ) qui, avec les définitions de préprocesseur appropriées, sont mappées aux `str` `_mbs` fonctions, ou `wcs` , selon le cas. Pour générer le MBCS, définissez le symbole `_MBCS` . Pour générer du code Unicode, définissez le symbole `_UNICODE` . Pour générer une application codée sur un octet, ne définissez ni l’un ni l’autres (valeur par défaut). Par défaut, `_UNICODE` est défini pour les applications MFC.

Le `_TCHAR` type de données est défini de manière conditionnelle dans Tchar. h. Si le symbole `_UNICODE` est défini pour votre Build, `_TCHAR` est défini comme **`wchar_t`** ; sinon, pour les builds sur un octet et MBCS, il est défini comme **`char`** . ( **`wchar_t`** , le type de données Unicode à caractères larges de base, est l’équivalent 16 bits d’un 8 bits **`signed char`** .) Pour les applications internationales, utilisez la `_tcs` famille de fonctions, qui fonctionnent en `_TCHAR` unités, pas en octets. Par exemple, `_tcsncpy` copies `n` `_TCHARs` , pas `n` octets.

Étant donné que certaines fonctions de gestion de chaîne SBCS (Single Byte Character Set) acceptent des paramètres (signés) **`char*`** , un type d’avertissement du compilateur ne peut pas être incompatible lorsque `_MBCS` est défini. Il existe trois façons d’éviter cet avertissement :

1. Utilisez les thunks de fonction inline de type sécurisé dans Tchar. h. Il s'agit du comportement par défaut.

1. Utilisez les macros directes dans Tchar. h en définissant `_MB_MAP_DIRECT` sur la ligne de commande. Ce faisant, vous devez associer manuellement les types. Il s’agit de la méthode la plus rapide, mais elle n’est pas de type sécurisé.

1. Utilisez les thunks de la fonction de bibliothèque liée statique de type sécurisé dans Tchar. h. Pour cela, définissez la constante `_NO_INLINING` sur la ligne de commande. Cette méthode est la plus lente, mais la plus sécurisée pour le type.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directives de préprocesseur pour les mappages de texte générique

|# définir|Version compilée|Exemple|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (caractères larges)|`_tcsrev` est mappé à `_wcsrev`|
|`_MBCS`|Caractères multioctets|`_tcsrev` est mappé à `_mbsrev`|
|Aucun (la valeur par défaut n’est ni `_UNICODE` `_MBCS` définie)|SBCS (ASCII)|`_tcsrev` est mappé à `strrev`|

Par exemple, la fonction de texte générique `_tcsrev` , qui est définie dans Tchar. h, est mappée à `_mbsrev` si vous avez défini `_MBCS` dans votre programme, ou à `_wcsrev` si vous avez défini `_UNICODE` . Sinon, `_tcsrev` est mappée à `strrev`. Les autres mappages de type de données sont fournis dans Tchar. h pour des raisons de commodité de programmation, mais `_TCHAR` est le plus utile.

### <a name="generic-text-data-type-mappings"></a>Mappages de types de données de texte générique

|Generic-Text<br /> Nom du type de données|_UNICODE &<br /> _MBCS non définie|_MBCS<br /> Défini|_UNICODE<br /> Défini|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`unsigned int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` ou `_TEXT`|Aucun effet (supprimé par le préprocesseur)|Aucun effet (supprimé par le préprocesseur)|`L` (convertit le caractère ou la chaîne suivant en son équivalent Unicode)|

Pour obtenir la liste des mappages de texte générique des routines, des variables et d’autres objets, consultez [mappages de texte générique](../c-runtime-library/generic-text-mappings.md) dans la référence de la bibliothèque de Run-Time.

> [!NOTE]
> N’utilisez pas la `str` famille de fonctions avec des chaînes Unicode, qui sont susceptibles de contenir des octets null incorporés. De même, n’utilisez pas la `wcs` famille de fonctions avec des chaînes MBCS (ou SBCS).

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

Si ni `_MBCS` ni `_UNICODE` n’ont été définis, le préprocesseur mappe le fragment au code ASCII codé sur un octet, comme suit :

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Par conséquent, vous pouvez écrire, gérer et compiler un fichier de code source unique à exécuter avec les routines spécifiques à l’un des trois types de jeux de caractères.

## <a name="see-also"></a>Voir aussi

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
[Utilisation de TCHAR. H (types de données avec _MBCS code)](../text/using-tchar-h-data-types-with-mbcs-code.md)
