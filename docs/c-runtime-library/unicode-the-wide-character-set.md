---
title: 'Unicode : jeu de caractères larges'
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 3a0c5698544c72e19feea8f35b7f5a516d95d561
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444488"
---
# <a name="unicode-the-wide-character-set"></a>Unicode : jeu de caractères larges

Un caractère large est un code de caractère multilingue de 2 octets. Partout dans le monde, tous les caractères utilisés dans l'informatique moderne, y compris les symboles techniques et les caractères d'édition spéciaux, peuvent être représentés conformément à la spécification Unicode sous la forme d'un caractère large. Développée et gérée par un vaste consortium qui inclut Microsoft, la norme Unicode est désormais largement acceptée.

Un caractère large est de type **wchar_t**. Une chaîne de caractères larges est représentée sous la forme d’un tableau **wchar_t[]** et est pointée par un pointeur `wchar_t*`. Vous pouvez représenter tout caractère ASCII sous la forme d’un caractère large en lui ajoutant la lettre **L** comme préfixe. Par exemple, L'\0' est le caractère null large (16 bits) de fin. De même, vous pouvez représenter toute chaîne ASCII sous la forme d'un littéral de chaîne à caractères larges simplement en ajoutant la lettre L comme préfixe au littéral ASCII (L"Hello").

En règle générale, les caractères larges prennent plus d'espace en mémoire que les caractères multioctets mais sont plus rapides à traiter. En outre, un seul paramètre régional peut être représenté à la fois dans un encodage multioctet, tandis que tous les jeux de caractères du monde sont représentés simultanément par la représentation Unicode.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)<br/>
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
