---
title: Caractères Unicode et définir la prise en charge (MBCS) | Microsoft Docs
ms.custom: ''
ms.date: 1/09/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e9d212e74f77d21efa1b2ed030f8a1446d111fc
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882947"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Prise en charge des jeux de caractères Unicode et MBCS (Multibyte Character Set)

Certains langages, par exemple, japonais et chinois, ont des grands jeux de caractères. Pour prendre en charge la programmation de ces marchés, les MFC Microsoft Foundation Class Library () permet à deux approches différentes pour la gestion des jeux de caractères volumineux :

- [Unicode](#mfc-support-for-unicode-strings), `wchar_t` en caractères larges et des chaînes encodées au format UTF-16.

- [Jeux de caractères multioctets (MBCS)](#mfc-support-for-mbcs-strings), **char** en fonction des caractères d’uniques ou sur deux octets et des chaînes encodées dans un jeu de caractères de paramètres régionaux spécifiques.

Microsoft a recommandé les bibliothèques MFC Unicode pour tout nouveau développement et les bibliothèques MBCS ont été dépréciées dans Visual Studio 2013 et Visual Studio 2015. Cela n'est plus le cas. Les avertissements de désapprobation MBCS ont été supprimés dans Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Prise en charge MFC pour les chaînes Unicode

La bibliothèque de classes MFC entière est conditionnellement activée pour les caractères Unicode et les chaînes stockées en caractères larges en tant que UTF-16. En particulier, la classe [CString](../atl-mfc-shared/reference/cstringt-class.md) prend en charge Unicode.

Ces bibliothèque, débogueur et fichiers DLL sont utilisés pour prendre en charge Unicode dans MFC :

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW. PDB|UAFXCWD. LIB|UAFXCWD. PDB|
|MFC*version*U.LIB|MFC*version*U.PDB|MFC*version*U.DLL|MFC*version*UD. LIB|
|MFC*version*UD. PDB|MFC*version*UD. DLL|MFCS*version*U.LIB|MFCS*version*U.PDB|
|MFCS*version*UD. LIB|MFCS*version*UD. PDB|MFCM*version*U.LIB|MFCM*version*U.PDB|
|MFCM*version*U.DLL|MFCM*version*UD. LIB|MFCM*version*UD. PDB|MFCM*version*UD. DLL|

(*version* représente le numéro de version du fichier ; par exemple, « 140 » signifie que la version 14.0.)

`CString` est basé sur le type de données TCHAR. Si le symbole _UNICODE est défini pour une build de votre programme, TCHAR est défini en tant que type `wchar_t`, un type de codage de caractères de 16 bits. Sinon, TCHAR est défini en tant que **char**, l’encodage de caractères 8 bits normal. Par conséquent, sous Unicode, un `CString` est composé de caractères de 16 bits. Sans Unicode, il est composé de caractères de type **char**.

Pour compléter la programmation Unicode de votre application, vous devez également :

- Utilisez la macro _T de manière conditionnelle des chaînes littérales code soit portable au format Unicode.

- Quand vous passez des chaînes, faites attention à déterminer si les arguments de fonction exigent une longueur en caractères ou une longueur en octets. La différence est importante si vous utilisez des chaînes Unicode.

- Utilisez des versions portables des fonctions de gestion des chaînes runtime C.

- Utiliser les types de données suivants pour les caractères et des pointeurs de caractères :

   - Utilisez TCHAR où vous utiliseriez **char**.

   - Utilisez LPTSTR où vous utiliseriez **char\***.

   - Utiliser LPCTSTR où vous utiliseriez **const char\***. `CString` fournit l’opérateur LPCTSTR pour convertir entre `CString` et LPCTSTR.

`CString` fournit également les prenant en charge Unicode des constructeurs, des opérateurs d’assignation et des opérateurs de comparaison.

Le [Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md) définit les versions portables de toutes ses fonctions de gestion des chaînes. Pour plus d’informations, voir la catégorie [internationalisation](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Prise en charge MFC pour les chaînes MBCS

La bibliothèque de classes est également activée pour les jeux de caractères multioctets, mais uniquement pour les caractères codés sur deux définit (DBCS).

Dans un jeu de caractères multioctets, un caractère peut être un ou deux octets. S’il s’agit de deux octets, le premier octet est un « octet de tête » spécial qui est choisi à partir d’une plage particulière, en fonction du code page est en cours d’utilisation. Prises ensemble, le responsable et les « octets de fin » spécifier un encodage de caractères uniques.

Si le symbole _MBCS est défini pour une build de votre programme, TCHAR, de type sur lequel `CString` est basée, est mappé à **char**. Il vous incombe de déterminer les octets dans un `CString` octets de tête des octets de la piste. La bibliothèque Runtime C fournit des fonctions pour vous aider à déterminer.

Sous DBCS, une chaîne donnée peut contenir tous les caractères de ANSI codés sur un octet, tous les caractères codés sur deux ou une combinaison des deux. Ces possibilités requièrent une attention particulière lors de l’analyse de chaînes. Cela inclut `CString` objets.

> [!NOTE]
> Sérialisation des chaînes Unicode dans MFC peut lire des chaînes Unicode et MBCS, quel que soit la version de l’application que vous exécutez. Vos fichiers de données sont portables entre les versions Unicode et MBCS de votre programme.

`CString` fonctions membres utilisent des versions « texte générique » spéciales des fonctions runtime C qu'ils appellent, ou ils utilisent des fonctions compatibles Unicode. Par conséquent, par exemple, si un `CString` fonction appelez généralement `strcmp`, il appelle la fonction de texte générique correspondante `_tcscmp` à la place. Selon la façon dont les symboles _MBCS et _UNICODE sont définis, `_tcscmp` mappe comme suit :

|||
|-|-|
|_MBCS défini|`_mbscmp`|
|_UNICODE défini|`wcscmp`|
|Aucun symbole défini|`strcmp`|

> [!NOTE]
> Les symboles _MBCS et _UNICODE s’excluent mutuellement.

Mappages de fonction de texte générique pour toutes les routines de gestion des chaînes d’exécution sont abordées dans [C Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md). Pour obtenir la liste, consultez [internationalisation](../c-runtime-library/internationalization.md).

De même, `CString` méthodes sont implémentées à l’aide des mappages de types de données génériques. Pour activer MBCS et Unicode, MFC utilise TCHAR pour **char** ou `wchar_t`, LPTSTR pour **char\***  ou `wchar_t*`et LPCTSTR pour **const char\***  ou `const wchar_t*`. Cela permet de garantir les mappages corrects pour MBCS ou Unicode.

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Manipulation de chaînes](../c-runtime-library/string-manipulation-crt.md)  
