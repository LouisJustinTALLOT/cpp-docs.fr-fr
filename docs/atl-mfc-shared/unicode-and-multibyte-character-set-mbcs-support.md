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
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317435"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Prise en charge des jeux de caractères Unicode et MBCS (Multibyte Character Set)

Certaines langues, par exemple, le japonais et le chinois, ont de grands ensembles de caractères. Pour soutenir la programmation de ces marchés, la Microsoft Foundation Class Library (MFC) permet deux approches différentes pour gérer les grands ensembles de personnages :

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` , basé sur les caractères larges et les cordes codées sous le forme d’UTF-16.

- [Multibyte Character Sets (MBCS)](#mfc-support-for-mbcs-strings), **caractères** et cordes simples ou doubles encodés dans un ensemble de personnages spécifiques à un endroit.

Microsoft a recommandé les bibliothèques MFC Unicode pour tout nouveau développement, et les bibliothèques MBCS ont été dépréciées dans Visual Studio 2013 et Visual Studio 2015. Cela n’est plus le cas. Les avertissements de dépréciation de MBCS ont été supprimés dans Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Support MFC pour les chaînes Unicode

Toute la bibliothèque de classe MFC est conditionnellement activée pour les caractères et les cordes Unicode stockés en caractères larges sous forme UTF-16. En particulier, la classe [CString](../atl-mfc-shared/reference/cstringt-class.md) est compatible Unicode.

Ces fichiers bibliothèque, débbugger et DLL sont utilisés pour prendre en charge Unicode dans MFC :

|||||
|-|-|-|-|
|UAFXCW. Lib|UAFXCW. Apb|UAFXCWD. Lib|UAFXCWD. Apb|
|MFC*version*U.LIB|MFC*version*U.PDB|MFC*version*U.DLL|MFC*version*UD. Lib|
|MFC*version*UD. Apb|MFC*version*UD. DLL DLL|MFCS*version*U.LIB|MFCS*version*U.PDB|
|MFCS*version*UD. Lib|MFCS*version*UD. Apb|MFCM*version*U.LIB|MFCM*version*U.PDB|
|MFCM*version*U.DLL|MFCM*version*UD. Lib|MFCM*version*UD. Apb|MFCM*version*UD. DLL DLL|

(*la version* représente le numéro de version du fichier; par exemple, '140' signifie version 14.0.)

`CString`est basé sur le type de données TCHAR. Si le symbole _UNICODE est défini pour une version de votre `wchar_t`programme, TCHAR est défini comme type , un type d’encodage de caractère 16 bits. Sinon, TCHAR est défini comme **char**, l’encodage de caractère 8 bits normal. Par conséquent, sous `CString` Unicode, a est composé de caractères 16 bits. Sans Unicode, il est composé de personnages de type **char**.

Pour compléter la programmation Unicode de votre application, vous devez également :

- Utilisez la macro _T pour coder sous condition les chaînes littérales pour être portables à Unicode.

- Lorsque vous passez des ficelles, faites attention à savoir si les arguments de fonction nécessitent une longueur dans les caractères ou une longueur dans les octets. La différence est importante si vous utilisez des chaînes Unicode.

- Utilisez des versions portables des fonctions de manipulation des chaînes C en temps d’exécution.

- Utilisez les types de données suivants pour les caractères et les pointeurs de caractères :

  - Utilisez TCHAR où vous utiliseriez **char**.

  - Utilisez LPTSTR où vous utiliseriez **char**<strong>\*</strong>.

  - Utilisez LPCTSTR où vous utiliseriez **const char**<strong>\*</strong>. `CString`fournit à l’opérateur LPCTSTR de convertir entre `CString` et LPCTSTR.

`CString`fournit également des constructeurs, des opérateurs d’affectation et des opérateurs de comparaison unicode.

Le [Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md) définit les versions portables de toutes ses fonctions de manipulation des cordes. Pour plus d’informations, voir la catégorie [Internationalisation](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Soutien MFC pour les chaînes MBCS

La bibliothèque de classe est également activée pour les ensembles de caractères multioctets, mais uniquement pour les ensembles de caractères double-byte (DBCS).

Dans un ensemble de caractères multioctets, un personnage peut être large d’un ou deux octets. S’il est large de deux octets, son premier octet est un « octet » spécial qui est choisi à partir d’une gamme particulière, selon la page de code utilisée. Pris ensemble, le plomb et les « octets de piste » spécifier un caractère unique codage.

Si le symbole _MBCS est défini pour une construction de votre `CString` programme, tapeZ TCHAR, sur lequel est basé, cartes à **char**. C’est à vous de déterminer `CString` quels octets dans un sont des octets en plomb et qui sont des octets de piste. La bibliothèque C run-time fournit des fonctions pour vous aider à déterminer cela.

Sous DBCS, une chaîne donnée peut contenir tous les caractères ANSI uni-byte, tous les caractères double-byte, ou une combinaison des deux. Ces possibilités nécessitent un soin particulier dans l’analyse des cordes. Cela `CString` inclut les objets.

> [!NOTE]
> La sérialisation des chaînes Unicode dans MFC peut lire les chaînes Unicode et MBCS quelle que soit la version de l’application que vous exécutez. Vos fichiers de données sont portables entre les versions Unicode et MBCS de votre programme.

`CString`les fonctions des membres utilisent des versions spéciales de « texte générique » des fonctions C run-time qu’ils appellent, ou ils utilisent des fonctions Unicode-consciente. Par conséquent, par `CString` exemple, si `strcmp`une fonction appelle généralement, `_tcscmp` il appelle la fonction générique-texte correspondante à la place. Selon la façon dont les symboles _MBCS et `_tcscmp` _UNICODE sont définis, les cartes comme suit:

|||
|-|-|
|_MBCS défini|`_mbscmp`|
|_UNICODE défini|`wcscmp`|
|Ni l’un ni l’autre symbole défini|`strcmp`|

> [!NOTE]
> Les symboles _MBCS et _UNICODE s’excluent mutuellement.

Les cartographies de fonction génériques pour toutes les routines de manipulation des chaînes en temps d’exécution sont discutées dans [C Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md). Pour une liste, voir [Internationalisation](../c-runtime-library/internationalization.md).

De `CString` même, les méthodes sont mises en œuvre en utilisant des cartes génériques de type de données. Pour activer À la fois MBCS et Unicode, MFC utilise TCHAR pour **l’omble chevalier** ou, `wchar_t`LPTSTR pour **l’omble chevalier** <strong>\*</strong> ou `wchar_t*`, et le LPCTSTR pour **l’omble ou** <strong>\*</strong> `const wchar_t*`. Ceux-ci assurent les cartes correctes pour MBCS ou Unicode.

## <a name="see-also"></a>Voir aussi

[Cordes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulation des cordes](../c-runtime-library/string-manipulation-crt.md)
