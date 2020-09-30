---
title: 'Unicode : jeu de caractères larges'
description: Introduction au jeu de caractères larges Unicode dans le runtime C de Microsoft.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 751017a62a960eaf2afa2354a43a13971b89252a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590158"
---
# <a name="unicode-the-wide-character-set"></a>Unicode : jeu de caractères larges

Un caractère large est un code de caractère multilingue de 2 octets. Partout dans le monde, tous les caractères utilisés dans l'informatique moderne, y compris les symboles techniques et les caractères d'édition spéciaux, peuvent être représentés conformément à la spécification Unicode sous la forme d'un caractère large. Développée et gérée par un vaste consortium qui inclut Microsoft, la norme Unicode est désormais largement acceptée.

Un caractère élargi est de type **`wchar_t`** . Une chaîne de caractères larges est représentée sous la forme d’un **`wchar_t[]`** tableau. Vous pointez sur le tableau avec un `wchar_t*` pointeur. 

Vous pouvez représenter n’importe quel caractère ASCII sous la forme d’un caractère élargi en préfixant la lettre `L` . Par exemple, `L'\0'` est le caractère null de fin (16 bits).

Vous pouvez représenter n’importe quel littéral de chaîne ASCII sous la forme d’un littéral de chaîne à caractères larges en préfixant la lettre `L` . Par exemple : `L"Hello"`.

En règle générale, les caractères larges utilisent plus d’espace en mémoire que les caractères multioctets. Mais les caractères larges sont plus rapides à traiter. Un seul paramètre régional peut être représenté à la fois dans l’encodage multioctet. Tous les jeux de caractères du monde sont représentés simultanément par la représentation Unicode.

## <a name="see-also"></a>Voir aussi

[Internationalisation](../c-runtime-library/internationalization.md)\
[Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)
