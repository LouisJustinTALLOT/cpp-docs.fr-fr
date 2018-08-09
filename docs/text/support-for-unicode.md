---
title: Prise en charge Unicode | Microsoft Docs
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53c71e1efad109daea689725ebbbb7dd9b100d30
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020169"
---
# <a name="support-for-unicode"></a>Prise en charge pour Unicode

Unicode est une spécification pour prendre en charge tous les jeux de caractères, y compris ceux qui ne peut pas être représentée dans qu’un octet (autrement dit, la plupart d'entre eux). Si vous programmez pour un marché international, nous vous recommandons d’utiliser Unicode ou un [jeu de caractères multioctets](../text/support-for-multibyte-character-sets-mbcss.md) (MBCS), ou code de votre programme afin de générer en modifiant un commutateur.

Un caractère large est un code de caractère multilingue de 2 octets. Des dizaines de milliers de caractères, comprenant presque tous les caractères utilisés dans l’informatique moderne, y compris les symboles techniques et les caractères d’édition spéciaux, peuvent être représentées selon la spécification Unicode en tant que l’échelle un seul caractère encodé par à l’aide de UTF-16. Les caractères qui ne peut pas être représentées dans un seul caractère large peuvent être représentés dans une paire Unicode à l’aide de la fonctionnalité de paire de substitution Unicode. Étant donné que pratiquement tous les caractères en cours d’utilisation courants sont représentée au format UTF-16 dans un caractère large unique de 16 bits, à l’aide de caractères larges simplifie la programmation avec les jeux de caractères internationaux. Caractères larges codés à l’aide de UTF-16LE (pour little-endian) constituent le format de caractères natif pour Windows.

Une chaîne de caractères larges est représentée sous la forme d'un tableau `wchar_t[]` et est pointée par un pointeur `wchar_t*`. Il est possible de représenter tout caractère ASCII sous la forme d'un caractère large en lui ajoutant la lettre L comme préfixe. Par exemple, L '\0' est le caractère NULL de fin à l’échelle (16 bits). De même, il est possible de représenter toute chaîne ASCII sous la forme d'un littéral de chaîne à caractères larges en ajoutant la lettre L comme préfixe au littéral ASCII (L"Hello").

En règle générale, les caractères larges prennent plus d'espace en mémoire que les caractères multioctets mais sont plus rapides à traiter. En outre, seul un paramètre régional peut être représenté à la fois dans un encodage multioctet, tandis que les jeux de tous les caractères dans le monde sont représentés simultanément par la représentation Unicode.

Toute l'infrastructure MFC prend en charge la spécification Unicode, et MFC permet la prise en charge d'Unicode en utilisant des macros portables, comme illustré dans le tableau ci-dessous.

## <a name="portable-data-types-in-mfc"></a>Types de données portables dans MFC

|Type de données non portables|Remplacé par cette macro|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`, `LPSTR` (Type de données Win32), `LPWSTR`|`LPTSTR`|
|`const char*`, `LPCSTR` (Type de données Win32), `LPCWSTR`|`LPCTSTR`|

Classe `CString` utilise `_TCHAR` comme base et fournit des constructeurs et des opérateurs pour simplifier les conversions. Il est possible d'écrire la plupart des opérations de chaînes pour Unicode en utilisant la même logique que celle utilisée pour traiter le jeu de caractères Windows ANSI, si ce n'est que l'unité d'opération élémentaire est un caractère de 16 bits à la place d'un octet de 8 bits. Contrairement à l'utilisation de jeux de caractères multioctets, vous n'avez pas à (et ne devriez pas) traiter un caractère Unicode comme s'il s'agissait de deux octets distincts. Toutefois, vous possédez traiter avec la possibilité d’un seul caractère représenté par une paire de substitution de caractères larges. En règle générale, n’écrivez pas de code qui suppose que la longueur d’une chaîne est le même que le nombre de caractères, si étroite ou étendue, qu’il contient.

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

- [Utiliser Unicode MFC et caractères multioctets (MBCS) pris en charge](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [Activer Unicode dans mon programme](../text/international-enabling.md)

- [Activer Unicode et MBCS dans mon programme](../text/internationalization-strategies.md)

- [Utiliser Unicode pour créer un programme internationalisé](../text/unicode-programming-summary.md)

- [Découvrez les avantages d’Unicode](../text/benefits-of-character-set-portability.md)

- [Utiliser wmain afin de passer des arguments à caractère élargi à mon programme](../text/support-for-using-wmain.md)

- [Consultez un résumé de la programmation Unicode](../text/unicode-programming-summary.md)

- [En savoir plus sur les mappages de texte générique pour la portabilité de la largeur en octets](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>Voir aussi
 [Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)  
 [Prise en charge de l’utilisation de wmain](../text/support-for-using-wmain.md)  