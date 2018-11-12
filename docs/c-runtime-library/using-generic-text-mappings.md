---
title: Utilisation des mappages de texte générique
ms.date: 11/04/2016
f1_keywords:
- _UNICODE
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
ms.openlocfilehash: b39e8563797ca0b57b54d2c85f851c8c45b29905
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471446"
---
# <a name="using-generic-text-mappings"></a>Utilisation des mappages de texte générique

**Section spécifique à Microsoft**

Pour simplifier le développement de code pour les marchés internationaux, la bibliothèque Runtime Microsoft fournit des mappages de « texte générique » spécifiques à Microsoft pour de nombreux types de données, routines et autres objets. Ces mappages sont définis dans TCHAR.H. Vous pouvez utiliser ces mappages de nom pour écrire du code générique qui peut être compilé pour n’importe lequel des trois types de jeux de caractères : ASCII (SBCS), MBCS ou Unicode, en fonction d’une constante manifeste que vous définissez à l’aide d’une instruction `#define`. Les mappages de texte générique sont des extensions Microsoft non compatibles ANSI.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directives de préprocesseur pour les mappages de texte générique

|#define|Version compilée|Exemple|
|--------------|----------------------|-------------|
|`_UNICODE`|Unicode (caractères larges)|`_tcsrev` correspond à `_wcsrev`|
|`_MBCS`|Caractères multioctets|`_tcsrev` correspond à `_mbsrev`|
|Aucun (la valeur par défaut : ni `_UNICODE` ni `_MBCS` défini)|SBCS (ASCII)|`_tcsrev` correspond à `strrev`|

Par exemple, la fonction de texte générique `_tcsrev`, définie dans TChar.h, est mappée à `mbsrev` si `MBCS` a été défini dans votre programme, ou à `_wcsrev` si `_UNICODE` a été défini. Sinon, `_tcsrev` est mappée à `strrev`.

Le type de données texte générique `_TCHAR`, également défini dans TCHAR.H, correspond au type `char` si `_MBCS` est défini, au type `wchar_t` si `_UNICODE` est défini et au type `char` si aucune constante n’est définie. Les autres mappages de type de données sont fournis dans TCHAR.H pour faciliter la programmation, mais `_TCHAR` est le type le plus utile.

### <a name="generic-text-data-type-mappings"></a>Mappages de types de données de texte générique

|Nom de type de données de texte générique|SBCS (_UNICODE, _MBCS non définis)|_MBCS défini|_UNICODE défini|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|`char`|`char`|`wchar_t`|
|`_TINT`|`int`|`int`|`wint_t`|
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|
|`_T` ou `_TEXT`|Aucun effet (supprimé par le préprocesseur)|Aucun effet (supprimé par le préprocesseur)|`L` (convertit le caractère suivant ou la chaîne suivante en son équivalent Unicode)|

Pour obtenir une liste complète des mappages de texte générique de routines, variables et autres objets, consultez [Mappages de texte générique](../c-runtime-library/generic-text-mappings.md).

Les fragments de code suivants illustrent l’utilisation de `_TCHAR` et `_tcsrev` pour le mappage sur les modèles MBCS, Unicode et SBCS.

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Si `MBCS` a été défini, le préprocesseur mappe le fragment précédent sur le code suivant :

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Si `_UNICODE` a été défini, le préprocesseur mappe le même fragment sur le code suivant :

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Si ni `_MBCS` ni `_UNICODE` n’ont été définis, le préprocesseur mappe le fragment sur le code ASCII sur un seul octet, comme suit :

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

Par conséquent, vous pouvez écrire, maintenir et compiler un fichier de code source unique à exécuter avec des routines qui sont spécifiques à un des trois types de jeu de caractères.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mappages de texte générique](../c-runtime-library/generic-text-mappings.md)<br/>
[Mappages de types de données](../c-runtime-library/data-type-mappings.md)<br/>
[Mappages de constantes et de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Mappages de routine](../c-runtime-library/routine-mappings.md)<br/>
[Exemple de programme de texte générique](../c-runtime-library/a-sample-generic-text-program.md)