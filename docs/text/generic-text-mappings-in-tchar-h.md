---
title: Mappages de texte générique dans tchar.h
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
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361341"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mappages de texte générique dans tchar.h

Pour simplifier le transport de code à usage international, la bibliothèque Microsoft run-time fournit des cartographies de texte générique spécifiques à Microsoft pour de nombreux types de données, routines et autres objets. Vous pouvez utiliser ces cartes, qui sont définies dans tchar.h, pour écrire du code générique qui peut être compilé pour les ensembles `#define` de caractères uni-byte, multioctets ou Unicode, selon une constante manifeste que vous définissez à l’aide d’une déclaration. Les mappages de texte générique sont des extensions Microsoft non compatibles ANSI.

En utilisant le tchar.h, vous pouvez créer des applications mono-byte, Multibyte Character Set (MBCS) et Unicode à partir des mêmes sources. tchar.h définit les macros (qui `_tcs`ont le préfixe ) qui, `str`avec `_mbs`les `wcs` définitions préprocessoires correctes, la carte à , , ou les fonctions, le cas échéant. Pour construire MBCS, `_MBCS`définissez le symbole . Pour construire Unicode, `_UNICODE`définissez le symbole . Pour créer une application unique, définissez ni l’un ni l’autre (la valeur par défaut). Par défaut, `_UNICODE` est défini pour les applications MFC.

Le `_TCHAR` type de données est défini sous condition dans tchar.h. Si le `_UNICODE` symbole est défini `_TCHAR` pour votre construction, est défini comme **wchar_t**; sinon, pour un seul-byte et MBCS construit, il est défini comme **char**. (**wchar_t**, le type de données de base Unicode à caractère large, est la contrepartie 16 bits à un char signé 8 **bits**.) Pour les applications `_tcs` internationales, utilisez la `_TCHAR` famille des fonctions, qui opèrent dans des unités, et non des octets. Par `_tcsncpy` exemple, `n` `_TCHARs`les `n` copies , pas les octets.

Parce que certaines fonctions de manipulation des chaînes Single Byte `char*` Character Set (SBCS) prennent des `_MBCS` paramètres (signés), un type de compileur de compileur résulte lorsqu’il est défini. Il y a trois façons d’éviter cet avertissement :

1. Utilisez les thunks de fonction inline de type-safe dans tchar.h. Il s'agit du comportement par défaut.

1. Utilisez les macros directes dans `_MB_MAP_DIRECT` tchar.h en définissant sur la ligne de commande. Ce faisant, vous devez associer manuellement les types. C’est la méthode la plus rapide, mais n’est pas sans danger de type.

1. Utilisez les thunks de fonction de bibliothèque reliés statiquement sûrs dans tchar.h. Pour cela, définissez la constante `_NO_INLINING` sur la ligne de commande. Cette méthode est la plus lente, mais la plus sécurisée pour le type.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directives de préprocesseur pour les mappages de texte générique

|Définir|Version compilée|Exemple|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (caractères larges)|`_tcsrev` correspond à `_wcsrev`|
|`_MBCS`|Caractères multioctets|`_tcsrev` correspond à `_mbsrev`|
|Aucun (la valeur `_UNICODE` `_MBCS` par défaut n’a ni ni définie)|SBCS (ASCII)|`_tcsrev` correspond à `strrev`|

Par exemple, la fonction `_tcsrev`de texte générique , qui est `_mbsrev` définie `_MBCS` dans tchar.h, cartes à si vous définissez dans votre programme, ou à `_wcsrev` si vous définissez `_UNICODE`. Sinon, `_tcsrev` est mappée à `strrev`. D’autres cartes de type de données sont fournies `_TCHAR` dans tchar.h pour plus de commodité de programmation, mais sont les plus utiles.

### <a name="generic-text-data-type-mappings"></a>Mappages de types de données de texte générique

|Texte générique<br /> Nom de type de données|& _UNICODE<br /> _MBCS non définie|_MBCS<br /> Défini|_UNICODE<br /> Défini|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**Wchar_t**|
|`_TINT`|**int**|**nombre entier non signé**|`wint_t`|
|`_TSCHAR`|**signed char**|**signed char**|**Wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**Wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**Wchar_t**|
|`_T` ou `_TEXT`|Aucun effet (supprimé par le préprocesseur)|Aucun effet (supprimé par le préprocesseur)|`L`(convertit le personnage ou la chaîne suivant à son homologue Unicode)|

Pour une liste de cartographies de texte générique de routines, variables et autres objets, voir [les cartographies génériques-texte](../c-runtime-library/generic-text-mappings.md) dans la référence de bibliothèque Run-Time.

> [!NOTE]
> N’utilisez `str` pas la famille des fonctions avec des chaînes Unicode, qui sont susceptibles de contenir des octets nuls intégrés. De même, n’utilisez pas la `wcs` famille des fonctions avec les chaînes MBCS (ou SBCS).

Les fragments de code suivants illustrent l’utilisation de `_TCHAR` et `_tcsrev` pour le mappage sur les modèles MBCS, Unicode et SBCS.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Si `_MBCS` elle a été définie, le préprocesseur trace ce fragment à ce code :

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Si `_UNICODE` elle a été définie, le préprocesseur trace ce fragment à ce code :

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Si `_MBCS` ni `_UNICODE` ni n’ont été définis, le préprocesseur cartographie le fragment en code ASCII uni-byte, comme suit :

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Par conséquent, vous pouvez écrire, maintenir et compiler un fichier de code à source unique pour exécuter avec des routines qui sont spécifiques à l’un des trois types d’ensembles de caractères.

## <a name="see-also"></a>Voir aussi

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
[Utilisation de TCHAR. Types de données H avec code _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)
