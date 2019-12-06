---
title: Modificateurs propres à Microsoft
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 2d65c0fe99895949d537ccf4368df2add3ff91ad
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857422"
---
# <a name="microsoft-specific-modifiers"></a>Modificateurs propres à Microsoft

Cette section décrit les extensions C++ spécifiques à Microsoft dans les domaines suivants :

- [Adressage basé](based-addressing.md), pratique consistant à utiliser un pointeur comme base à partir de laquelle d’autres pointeurs peuvent être décalés

- [Conventions d’appel de fonction](calling-conventions.md)

- Attributs étendus de classe de stockage déclarés avec le mot clé [__declspec](declspec.md)

- Mot clé [__w64](w64.md)

## <a name="microsoft-specific-keywords"></a>mots clés spécifiques à Microsoft

Un grand nombre des mots clés spécifiques à Microsoft peuvent être utilisés pour modifier des déclarateurs afin de former des types dérivés. Pour plus d’informations sur les déclarateurs, consultez [déclarateurs](overview-of-declarators.md).

|Mot clé|Signification|Utilisé pour former des types dérivés ?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|Le nom qui suit déclare un décalage de 32 bits par rapport à la base 32 bits contenue dans la déclaration.|Oui|
|[__cdecl](cdecl.md)|Le nom qui suit utilise les conventions de nommage et d’appel du langage C.|Oui|
|[__declspec](declspec.md)|Le nom qui suit spécifie un attribut de classe de stockage spécifique à Microsoft.|Non|
|[__fastcall](fastcall.md)|Le nom qui suit déclare une fonction qui utilise des registres, lorsqu’ils sont disponibles, à la place de la pile, pour transmettre des arguments.|Oui|
|[__restrict](extension-restrict.md)|Semblable à __declspec ([restreindre](restrict.md)), mais pour une utilisation sur des variables.|Non|
|[__stdcall](stdcall.md)|Le nom qui suit spécifie une fonction qui respecte la convention d'appel standard.|Oui|
|[__w64](w64.md)|Marque un type de données comme étant plus grand sur un compilateur 64 bits.|Non|
|[__unaligned](unaligned.md)|Spécifie qu'un pointeur désignant un type ou d'autres données n'est pas aligné.|Non|
|[__vectorcall](vectorcall.md)|Le nom qui suit déclare une fonction qui utilise des registres, y compris les registres SSE lorsqu'ils sont disponibles, à la place de la pile, pour transmettre des arguments.|Oui|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur le langage C++](cpp-language-reference.md)
