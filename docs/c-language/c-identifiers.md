---
title: Identificateurs C
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, C
- naming identifiers
- identifiers
- symbols, C identifiers
- identifiers, case sensitivity
- symbols, case sensitivity
ms.assetid: d02edbbc-85a0-4118-997b-84ee6b972eb6
ms.openlocfilehash: d68eb690a19f57555d9d757a2f058692ea1a40c3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223744"
---
# <a name="c-identifiers"></a>Identificateurs C

Les « identificateurs » ou « symboles » sont des noms que vous fournissez pour des variables, des types, des fonctions et des étiquettes dans votre programme. Les noms d'identificateur doivent différer des mots clés en termes d'orthographe et de casse. Vous ne pouvez pas utiliser des mots clés (C ou Microsoft) en tant qu'identificateurs ; ils sont réservés à un usage spécial. Pour créer un identificateur, vous le spécifiez dans la déclaration d'une variable, d'un type ou d'une fonction. Dans cet exemple, `result` est un identificateur pour une variable de type entier, et `main` et `printf` sont des noms d'identificateur pour les fonctions.

```
#include <stdio.h>

int main()
{
    int result;

    if ( result != 0 )
        printf_s( "Bad file handle\n" );
}
```

Une fois l'identificateur déclaré, vous pouvez l'utiliser dans les instructions de programme ultérieures pour faire référence à la valeur associée.

Un type spécial d’identificateur, appelé étiquette d’instruction, peut être utilisé dans les **`goto`** instructions. (Les déclarations sont décrites dans [Déclarations et types](../c-language/declarations-and-types.md). Les étiquettes d'instructions sont décrites dans [Les instructions goto et étiquetées](../c-language/goto-and-labeled-statements-c.md).)

## <a name="syntax"></a>Syntaxe

*identificateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*caractère*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

*nondigit* : un des caractères suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ a b c d e f g h i j k l mn o p q r s t u v w x y z**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F G H I J K L MN O P Q R S T U V W X Y Z**

*digit* : un des caractères suivants<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

Le premier caractère d'un nom d'identificateur doit être `nondigit` (autrement dit, ce doit être un trait de soulignement ou une lettre majuscule ou minuscule). ANSI autorise six caractères significatifs dans un nom d'identificateur externe et 31 pour les noms des identificateurs internes (dans une fonction). Les identificateurs externes (ceux déclarés au niveau de la portée globale ou déclarés avec la classe de stockage **`extern`** ) peuvent être soumis à des restrictions d’affectation de noms supplémentaires, car ces identificateurs doivent être traités par d’autres logiciels tels que les liens.

**Spécifique à Microsoft**

Bien qu'ANSI autorise 6 caractères significatifs dans les noms d'identificateur externe et 31 pour les noms des identificateurs internes (dans une fonction), le compilateur C Microsoft autorise 247 caractères dans un nom d'identificateur interne ou externe. Si la compatibilité ANSI ne vous préoccupe pas, vous pouvez modifier cette valeur par défaut en définissant un nombre plus petit ou plus grand via l'option /H (restreindre la longueur des noms externes).

**FIN spécifique à Microsoft**

Le compilateur C considère les majuscules et les minuscules comme des caractères distincts. Cette fonctionnalité, appelée « respect de la casse », vous permet de créer des identificateurs distincts qui ont la même orthographe mais différentes casses pour une ou plusieurs des lettres. Par exemple, chacun de ces identificateurs suivants est unique :

```
add
ADD
Add
aDD
```

**Spécifique à Microsoft**

Pour les identificateurs, ne sélectionnez pas des noms qui commencent par deux traits de soulignement ou par un trait de soulignement suivi d'une majuscule. La norme C ANSI permet de réserver les noms d'identificateur qui commencent par ces combinaisons de caractères à une utilisation par le compilateur. Les identificateurs ayant une portée de niveau fichier ne doivent pas être précédés d'un trait de soulignement et d'une minuscule comme deux premières lettres. Les noms d'identificateur qui commencent par ces caractères sont également réservés. Par convention, Microsoft utilise un trait de soulignement et une majuscule au début des noms de macro, et des traits de soulignement doubles pour les noms de mot clé spécifiques de Microsoft. Pour éviter les conflits de noms, sélectionnez toujours des noms d'identificateur ne commençant pas par un ou deux traits de soulignement, ou des noms commençant par un trait de soulignement suivi d'une majuscule.

**FIN spécifique à Microsoft**

Voici quelques exemples d'identificateurs valides conformes aux restrictions d'affectation de noms ANSI ou Microsoft :

```
j
count
temp1
top_of_page
skip12
LastNum
```

**Spécifique à Microsoft**

Bien que les identificateurs dans les fichiers sources respectent la casse par défaut, les symboles dans les fichiers objets ne la respectent pas. Microsoft C traite les identificateurs d'une unité de compilation comme respectant la casse.

L'éditeur de liens Microsoft respecte la casse. Vous devez spécifier tous les identificateurs de manière cohérente selon le cas.

Le « jeu de caractères source » est le jeu de caractères reconnus qui peuvent figurer dans les fichiers sources. Pour Microsoft C, le jeu source est le jeu de caractères ASCII standard. Le jeu de caractères sources et le jeu de caractères d'exécution incluent les caractères ASCII utilisés en tant que séquences d'échappement. Consultez [Constantes caractères](../c-language/c-character-constants.md) pour plus d'informations sur le jeu de caractères d'exécution.

**FIN spécifique à Microsoft**

Un identificateur a une « portée », qui est la zone du programme dans laquelle il est connu, et une « liaison, » qui détermine si le même nom dans une autre portée fait référence à ce même identificateur. Ces rubriques sont expliquées dans [Durée de vie, portée, visibilité, et liaison](../c-language/lifetime-scope-visibility-and-linkage.md).

## <a name="see-also"></a>Voir aussi

[Éléments de C](../c-language/elements-of-c.md)
