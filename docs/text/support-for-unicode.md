---
title: Prise en charge pour Unicode
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: 0b61407920a0ce35a1c6a8466458736e983e271e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168562"
---
# <a name="support-for-unicode"></a>Prise en charge pour Unicode

Unicode est une spécification pour la prise en charge de tous les jeux de caractères, y compris ceux qui ne peuvent pas être représentés dans un seul octet.  Si vous programmez pour un marché international, nous vous recommandons d’utiliser Unicode ou un [jeu de caractères multioctets](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS). Ou bien, codez votre programme afin de pouvoir le générer pour soit en modifiant un commutateur.

Un caractère large est un code de caractère multilingue de 2 octets. Des dizaines de milliers de caractères, comprenant presque tous les caractères utilisés dans le monde informatique moderne, y compris les symboles techniques et les caractères de publication spéciaux, peuvent être représentés conformément à la spécification Unicode sous la forme d’un caractère unique encodé par en utilisant UTF-16. Les caractères qui ne peuvent pas être représentés dans un seul caractère élargi peuvent être représentés dans une paire Unicode à l’aide de la fonctionnalité de paire de substitution Unicode. Étant donné que presque tous les caractères de l’utilisation courante sont représentés en UTF-16 dans un seul caractère étendu de 16 bits, l’utilisation de caractères larges simplifie la programmation avec les jeux de caractères internationaux. Les caractères larges encodés à l’aide d’UTF-16LE (pour Little endian) sont le format de caractère natif pour Windows.

Une chaîne de caractères larges est représentée sous la forme d'un tableau `wchar_t[]` et est pointée par un pointeur `wchar_t*`. Il est possible de représenter tout caractère ASCII sous la forme d'un caractère large en lui ajoutant la lettre L comme préfixe. Par exemple, L'\0' est le caractère NULL large (16 bits) de fin. De même, il est possible de représenter toute chaîne ASCII sous la forme d'un littéral de chaîne à caractères larges en ajoutant la lettre L comme préfixe au littéral ASCII (L"Hello").

En règle générale, les caractères larges prennent plus d'espace en mémoire que les caractères multioctets mais sont plus rapides à traiter. En outre, un seul paramètre régional peut être représenté à la fois dans un encodage multioctet, tandis que tous les jeux de caractères du monde sont représentés simultanément par la représentation Unicode.

Toute l'infrastructure MFC prend en charge la spécification Unicode, et MFC permet la prise en charge d'Unicode en utilisant des macros portables, comme illustré dans le tableau ci-dessous.

## <a name="portable-data-types-in-mfc"></a>Types de données portables dans MFC

|Type de données non portables|Remplacé par cette macro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (type de données Win32), `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (type de données Win32), `LPCWSTR`|`LPCTSTR`|

La classe `CString` utilise `_TCHAR` comme base et fournit des constructeurs et des opérateurs pour faciliter les conversions. Il est possible d'écrire la plupart des opérations de chaînes pour Unicode en utilisant la même logique que celle utilisée pour traiter le jeu de caractères Windows ANSI, si ce n'est que l'unité d'opération élémentaire est un caractère de 16 bits à la place d'un octet de 8 bits. Contrairement à l'utilisation de jeux de caractères multioctets, vous n'avez pas à (et ne devriez pas) traiter un caractère Unicode comme s'il s'agissait de deux octets distincts. Toutefois, vous devez gérer la possibilité d’un caractère unique représenté par une paire de substitution de caractères larges. En général, n’écrivez pas de code qui suppose que la longueur d’une chaîne est le même que le nombre de caractères, qu’il soit étroit ou large, qu’il contient.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Utiliser la prise en charge d’Unicode et du jeu de caractères multioctets (MBCS) MFC](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Activer Unicode dans mon programme](../text/international-enabling.md)

- [Activer à la fois Unicode et MBCS dans mon programme](../text/internationalization-strategies.md)

- [Utiliser Unicode pour créer un programme international](../text/unicode-programming-summary.md)

- [Découvrez les avantages d’Unicode](../text/benefits-of-character-set-portability.md)

- [Utiliser wmain pour passer des arguments à caractères larges à mon programme](../text/support-for-using-wmain.md)

- [Afficher un résumé de la programmation Unicode](../text/unicode-programming-summary.md)

- [En savoir plus sur les mappages de texte générique pour la portabilité à largeur d’octet](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Voir aussi

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
[Prise en charge de l’utilisation de wmain](../text/support-for-using-wmain.md)
