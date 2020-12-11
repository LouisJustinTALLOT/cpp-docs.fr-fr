---
description: 'En savoir plus sur : modificateurs spécifiques à Microsoft'
title: Modificateurs propres à Microsoft
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: dd82bf22da99e864a7b4898da1a99a12c3ad3de4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161622"
---
# <a name="microsoft-specific-modifiers"></a>Modificateurs propres à Microsoft

Cette section décrit les extensions C++ spécifiques à Microsoft dans les domaines suivants :

- [Adressage basé](based-addressing.md), pratique consistant à utiliser un pointeur comme base à partir de laquelle d’autres pointeurs peuvent être décalés

- [Conventions d'appel de fonction](calling-conventions.md)

- Attributs étendus de classe de stockage déclarés avec le mot clé [__declspec](declspec.md)

- Mot clé [__w64](w64.md)

## <a name="microsoft-specific-keywords"></a>mots clés spécifiques à Microsoft

Un grand nombre des mots clés spécifiques à Microsoft peuvent être utilisés pour modifier des déclarateurs afin de former des types dérivés. Pour plus d’informations sur les déclarateurs, consultez [déclarateurs](./declarations-and-definitions-cpp.md).

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
