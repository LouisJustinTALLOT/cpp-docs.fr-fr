---
title: Prise en charge des jeux de caractères Unicode et MBCS (Multibyte Character Set)
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: 217690e09ed595bb9fa9572693bf774259c42412
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219025"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Prise en charge des jeux de caractères Unicode et MBCS (Multibyte Character Set)

Certains langages, par exemple, le japonais et le chinois, possèdent de grands jeux de caractères. Pour prendre en charge la programmation pour ces marchés, le bibliothèque MFC (Microsoft Foundation Class) (MFC) permet deux approches différentes de la gestion des jeux de caractères volumineux :

- [Unicode](#mfc-support-for-unicode-strings), **`wchar_t`** caractères larges et chaînes encodés au format UTF-16.

- [Jeux de caractères multioctets (MBCS)](#mfc-support-for-mbcs-strings), **`char`** caractères uniques ou codés sur deux octets et chaînes encodés dans un jeu de caractères spécifique aux paramètres régionaux.

Microsoft a recommandé les bibliothèques Unicode MFC pour tout nouveau développement, et les bibliothèques MBCS étaient dépréciées dans Visual Studio 2013 et Visual Studio 2015. Cela n'est plus le cas. Les avertissements de désapprobation MBCS ont été supprimés dans Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Prise en charge MFC pour les chaînes Unicode

L’ensemble de la bibliothèque de classes MFC est activé de manière conditionnelle pour les chaînes et les caractères Unicode stockés dans des caractères larges au format UTF-16. En particulier, la classe [CString](../atl-mfc-shared/reference/cstringt-class.md) est compatible Unicode.

Ces fichiers de bibliothèque, de débogueur et de DLL sont utilisés pour prendre en charge Unicode dans MFC :

|||||
|-|-|-|-|
|UAFXCW. LIB|UAFXCW. PDBONLY|UAFXCWD. LIB|UAFXCWD. PDBONLY|
|MFC*version*U. lib|MFC*version*U. pdb|*Version* MFCU.DLL|UD de*version*MFC. LIB|
|UD de*version*MFC. PDBONLY|*Version* MFCUD.DLL|MFCS*version*U. lib|MFCS*version*U. pdb|
|MFCS*version*ud. LIB|MFCS*version*ud. PDBONLY|MFCM*version*U. lib|MFCM*version*U. pdb|
|*Version* de MFCMU.DLL|MFCM*version*ud. LIB|MFCM*version*ud. PDBONLY|*Version* de MFCMUD.DLL|

(*version* représente le numéro de version du fichier ; par exemple, « 140 » correspond à la version 14,0.)

`CString`est basé sur le type de données TCHAR. Si le symbole _UNICODE est défini pour une génération de votre programme, TCHAR est défini en tant que type **`wchar_t`** , un type d’encodage de caractères de 16 bits. Dans le cas contraire, TCHAR est défini comme **`char`** , l’encodage de caractères standard de 8 bits. Par conséquent, sous Unicode, un `CString` est composé de caractères 16 bits. Sans Unicode, elle est composée de caractères de type **`char`** .

Pour effectuer la programmation Unicode de votre application, vous devez également :

- Utilisez la macro _T pour coder de manière conditionnelle des chaînes littérales pour qu’elles soient portables vers Unicode.

- Lorsque vous transmettez des chaînes, prêtez attention à déterminer si les arguments de fonction nécessitent une longueur en caractères ou une longueur en octets. La différence est importante si vous utilisez des chaînes Unicode.

- Utilisez des versions portables des fonctions de gestion des chaînes du runtime C.

- Utilisez les types de données suivants pour les caractères et les pointeurs de caractère :

  - Utilisez TCHAR à l’endroit où vous utiliseriez **`char`** .

  - Utilisez LPTSTR là où vous utiliseriez **`char`** <strong>\*</strong> .

  - Utilisez LPCTSTR là où vous utiliserez **const char** <strong>\*</strong> . `CString`fournit à l’opérateur LPCTSTR la conversion entre `CString` et LPCTSTR.

`CString`fournit également des constructeurs, des opérateurs d’assignation et des opérateurs de comparaison compatibles Unicode.

La [référence](../c-runtime-library/c-run-time-library-reference.md) de la bibliothèque Runtime définit les versions portables de toutes ses fonctions de gestion de chaînes. Pour plus d’informations, consultez l' [internationalisation](../c-runtime-library/internationalization.md)de la catégorie.

## <a name="mfc-support-for-mbcs-strings"></a>Prise en charge MFC pour les chaînes MBCS

La bibliothèque de classes est également activée pour les jeux de caractères multioctets, mais uniquement pour les jeux de caractères codés sur deux octets (DBCS).

Dans un jeu de caractères multioctets, un caractère peut avoir une largeur d’un ou de deux octets. S’il s’agit d’une largeur de deux octets, son premier octet est un « octet de tête » spécial qui est choisi dans une plage particulière, en fonction de la page de codes en cours d’utilisation. Pris ensemble, le lead et les « octets de fin » spécifient un encodage de caractères unique.

Si le symbole _MBCS est défini pour une génération de votre programme, le type TCHAR, sur lequel `CString` est basé, est mappé à **`char`** . C’est à vous de déterminer quels octets d’un `CString` sont les octets de tête et les octets de fin. La bibliothèque Runtime C fournit des fonctions pour vous aider à déterminer cela.

Sous DBCS, une chaîne donnée peut contenir tous les caractères ANSI codés sur un octet, tous les caractères codés sur deux octets ou une combinaison des deux. Ces possibilités nécessitent une attention particulière lors de l’analyse des chaînes. Cela comprend les `CString` objets.

> [!NOTE]
> La sérialisation de chaînes Unicode dans MFC peut lire des chaînes Unicode et MBCS, quelle que soit la version de l’application que vous exécutez. Vos fichiers de données sont portables entre les versions Unicode et MBCS de votre programme.

`CString`les fonctions membres utilisent des versions spéciales « texte générique » des fonctions runtime C qu’elles appellent, ou elles utilisent des fonctions compatibles Unicode. Par exemple, si une fonction appelle `CString` généralement `strcmp` , elle appelle la fonction de texte générique correspondante à la `_tcscmp` place. Selon la façon dont les symboles _MBCS et _UNICODE sont définis, `_tcscmp` correspond à ce qui suit :

|||
|-|-|
|_MBCS défini|`_mbscmp`|
|_UNICODE défini|`wcscmp`|
|Aucun symbole défini|`strcmp`|

> [!NOTE]
> Les symboles _MBCS et _UNICODE s’excluent mutuellement.

Les mappages de fonctions de texte générique pour toutes les routines de gestion de chaîne d’exécution sont décrits dans la référence de la [bibliothèque Runtime C](../c-runtime-library/c-run-time-library-reference.md). Pour obtenir une liste, consultez [internationalisation](../c-runtime-library/internationalization.md).

De même, `CString` les méthodes sont implémentées à l’aide de mappages de types de données génériques. Pour activer MBCS et Unicode, MFC utilise TCHAR pour **`char`** ou, **`wchar_t`** LPTStr pour **`char`** <strong>\*</strong> ou `wchar_t*` , et LPCTSTR pour **const char** <strong>\*</strong> ou `const wchar_t*` . Ils garantissent les mappages appropriés pour MBCS ou Unicode.

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulation de chaînes](../c-runtime-library/string-manipulation-crt.md)
