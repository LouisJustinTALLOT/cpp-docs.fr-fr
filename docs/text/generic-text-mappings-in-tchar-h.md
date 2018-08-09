---
title: Mappages de texte générique dans Tchar.h | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd66a0e2f45def3aa22342ca30eaa64846ebf4c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40012008"
---
# <a name="generic-text-mappings-in-tcharh"></a>Mappages de texte générique dans Tchar.h
Pour simplifier le transport de code pour une utilisation internationale, le [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] fournit de la bibliothèque du run-time [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)]-mappages de texte générique spécifiques pour nombreux types de données, routines et autres objets. Vous pouvez utiliser ces mappages, qui sont définis dans Tchar.h, pour écrire du code générique qui peut être compilé sur un octet, multioctet, ou [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] jeux, en fonction d’une constante de manifeste que vous définissez à l’aide de caractères un `#define` instruction. Mappages de texte générique sont [!INCLUDE[TLA#tla_ms](../text/includes/tlasharptla_ms_md.md)] extensions qui ne sont pas [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] compatible.  
  
 En utilisant le fichier Tchar.h, vous pouvez générer un octet, multioctets jeu de caractères (MBCS), et [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] applications à partir des mêmes sources. Tchar.h définit des macros (qui ont le préfixe `_tcs`) qui, avec les définitions de préprocesseur, correspondent aux `str`, `_mbs`, ou `wcs` fonctions, comme il convient. Pour générer du MBCS, définissez le symbole `_MBCS`. Pour générer [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)], définissez le symbole `_UNICODE`. Pour générer une application d’un octet, définissez ni (la valeur par défaut). Par défaut, `_MBCS` est défini pour les applications MFC.  
  
 Le `_TCHAR` type de données est défini de façon conditionnelle dans Tchar.h. Si le symbole `_UNICODE` est défini pour votre build, `_TCHAR` est défini comme **wchar_t**; sinon, pour un octet et MBCS builds, il est défini comme **char**. (**wchar_t**, type de données à caractère élargi Unicode de base, est l’équivalent de 16 bits de 8 bits signé **char**.) Dans les applications internationales, utilisez le `_tcs` famille de fonctions qui opèrent dans `_TCHAR` unités, non en octets. Par exemple, `_tcsncpy` copies `n` `_TCHARs`, et non `n` octets.  
  
 Étant donné que les fonctions de certains gestion de chaîne unique le définir de caractère octet (SBCS) (signé) `char*` paramètres, des résultats d’avertissement du compilateur une incompatibilité type lorsque `_MBCS` est défini. Il existe trois façons d’éviter cet avertissement :  
  
1.  Utilisez les thunks de la fonction inline de type sécurisé dans Tchar.h. Il s'agit du comportement par défaut.  
  
2.  Utilisez les macros directes dans Tchar.h en définissant `_MB_MAP_DIRECT` sur la ligne de commande. Ce faisant, vous devez associer manuellement les types. La méthode est plus rapide, ce n’est pas de type sécurisé.  
  
3.  Utilisez les thunks de fonction de bibliothèque liée statiquement de type sécurisé dans Tchar.h. Pour cela, définissez la constante `_NO_INLINING` sur la ligne de commande. Cette méthode est la plus lente, mais la plus sécurisée pour le type.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directives de préprocesseur pour les mappages de texte générique  
  
|# define|Version compilée|Exemple|  
|---------------|----------------------|-------------|  
|`_UNICODE`|[!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] (caractères larges)|`_tcsrev` correspond à `_wcsrev`|  
|`_MBCS`|Caractères multioctets|`_tcsrev` correspond à `_mbsrev`|  
|Aucun (la valeur par défaut ne possède aucun `_UNICODE` ni `_MBCS` défini)|SBCS ([!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)])|`_tcsrev` correspond à `strrev`|  
  
 Par exemple, la fonction de texte générique `_tcsrev`, qui est défini dans Tchar.h, correspond à `_mbsrev` si vous avez défini `_MBCS` dans votre programme, ou à `_wcsrev` si vous avez défini `_UNICODE`. Sinon, `_tcsrev` est mappée à `strrev`. Autres mappages de type de données sont fournis dans Tchar.h pour faciliter la programmation, mais `_TCHAR` est le plus utile.  
  
### <a name="generic-text-data-type-mappings"></a>Mappages de types de données de texte générique  
  
|Texte générique<br /><br /> Nom de Type de données|_UNICODE &AMP;<br /><br /> _MBCS non définis|_MBCS<br /><br /> Défini|_UNICODE<br /><br /> Défini|  
|--------------------------------------|----------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|**char**|**char**|**wchar_t**|  
|`_TINT`|**int**|**unsigned int**|`wint_t`|  
|`_TSCHAR`|**char signé**|**char signé**|**wchar_t**|  
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|  
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|  
|`_T` ou `_TEXT`|Aucun effet (supprimé par le préprocesseur)|Aucun effet (supprimé par le préprocesseur)|`L` (convertit le caractère ou chaîne à suivant son [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] équivalent)|  
  
 Pour obtenir la liste des mappages de texte générique des routines, variables et autres objets, consultez [mappages de texte générique](../c-runtime-library/generic-text-mappings.md) dans le Run-Time Library Reference.  
  
> [!NOTE]
>  N’utilisez pas le `str` famille de fonctions avec des chaînes Unicode, qui sont susceptibles de contenir des octets null incorporés. De même, n’utilisez pas le `wcs` famille de fonctions avec des chaînes MBCS (ou SBCS).  
  
 Les fragments de code suivants illustrent l’utilisation de `_TCHAR` et `_tcsrev` pour le mappage pour le MBCS, [!INCLUDE[TLA#tla_unicode](../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)]et les modèles SBCS.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Si `_MBCS` a été défini, le préprocesseur mappe ce fragment à ce code :  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Si `_UNICODE` a été défini, le préprocesseur mappe ce fragment à ce code :  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Si ni `_MBCS` ni `_UNICODE` ont été définis, le préprocesseur mappe le fragment sur un octet [!INCLUDE[TLA#tla_ascii](../text/includes/tlasharptla_ascii_md.md)] de code, comme suit :  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Par conséquent, vous pouvez écrire, maintenir et compiler un fichier de code source unique à exécuter avec des routines qui sont spécifiques à un des trois types de jeux de caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)   
 [Utilisation de types de données TCHAR.H avec _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)