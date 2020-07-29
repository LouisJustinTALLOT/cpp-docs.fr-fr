---
title: Spécificateurs de type C
ms.date: 01/29/2018
helpviewer_keywords:
- type specifiers, C
- specifiers, type
ms.assetid: fbe13441-04c3-4829-b047-06d374adc2b6
ms.openlocfilehash: 652388fdf345cab7878bbd8c054b769377b322a9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217153"
---
# <a name="c-type-specifiers"></a>Spécificateurs de type C

Les spécificateurs de type dans les déclarations définissent le type d'une variable ou d'une déclaration de fonction.

## <a name="syntax"></a>Syntaxe

*type-specifier*: &nbsp; &nbsp; &nbsp; &nbsp; **`void`** &nbsp; &nbsp; &nbsp; &nbsp; **`char`** &nbsp; &nbsp; &nbsp; &nbsp; **`short`** &nbsp; &nbsp; &nbsp; &nbsp; **`int`** &nbsp; &nbsp; &nbsp; &nbsp; **`long`** &nbsp; &nbsp; &nbsp; &nbsp; **`float`** &nbsp; &nbsp; &nbsp; &nbsp; **`double`** &nbsp; &nbsp; &nbsp; &nbsp; **`signed`** &nbsp; &nbsp; &nbsp; &nbsp; **`unsigned`** &nbsp; &nbsp; &nbsp; &nbsp; *struct-or-Union-specifier* &nbsp; &nbsp; &nbsp; &nbsp; *enum-specifier* &nbsp; &nbsp; &nbsp; &nbsp; *typedef-Name*

Les **`signed char`** **`signed int`** **`signed short int`** types int,, et **signés** , ainsi que leurs **`unsigned`** équivalents et **`enum`** , sont appelés types *intégraux* . Les **`float`** **`double`** **`long double`** spécificateurs de type, et sont appelés types à virgule *flottante* ou à *virgule flottante* . Vous pouvez utiliser n'importe quel spécificateur de type intégral ou à virgule flottante dans une variable ou une déclaration de fonction. Si aucun *type-specifier* n’est fourni dans une déclaration, il est considéré comme **`int`** .

Les mots clés facultatifs **`signed`** et **`unsigned`** peuvent précéder ou suivre l’un des types intégraux, sauf **`enum`** , et peuvent également être utilisés seuls comme spécificateurs de type, auquel cas ils sont compris comme **`signed int`** et **`unsigned int`** , respectivement. Lorsqu’il est utilisé seul, le mot clé **`int`** est supposé être **`signed`** . Lorsqu’ils sont utilisés seuls, les mots clés **`long`** et **`short`** sont compris comme **long int** et **`short int`** .

Les types énumération sont considérés comme des types de base. Les spécificateurs de type pour les types énumération sont traités dans [Déclarations d'énumération](../c-language/c-enumeration-declarations.md).

Le mot clé **`void`** a trois utilisations : pour spécifier un type de retour de fonction, pour spécifier une liste de types d’arguments pour une fonction qui n’accepte aucun argument et pour spécifier un pointeur vers un type non spécifié. Vous pouvez utiliser le **`void`** type pour déclarer des fonctions qui ne retournent aucune valeur ou pour déclarer un pointeur vers un type non spécifié. Pour [Arguments](../c-language/arguments.md) plus d’informations sur **`void`** lorsqu’il apparaît seul entre les parenthèses qui suivent un nom de fonction, consultez arguments.

**Spécifique à Microsoft**

La vérification de type est maintenant conforme à la norme ANSI, ce qui signifie que le type **`short`** et le type **`int`** sont des types distincts. Par exemple, voici une redéfinition dans le compilateur C Microsoft qui était acceptée par les versions précédentes du compilateur.

```C
int   myfunc();
short myfunc();
```

Cet exemple suivant génère également un avertissement concernant l'indirection vers différents types :

```C
int *pi;
short *ps;

ps = pi;  /* Now generates warning */
```

Le compilateur C Microsoft génère également des avertissements pour les différences de signe. Par exemple :

```C
signed int *pi;
unsigned int *pu

pi = pu;  /* Now generates warning */
```

**`void`** Les expressions de type sont évaluées pour les effets secondaires. Vous ne pouvez pas utiliser la valeur (inexistante) d’une expression qui a un type **`void`** de quelque façon que ce soit, ni convertir une **`void`** expression (par conversion implicite ou explicite) en n’importe quel type, sauf **`void`** . Si vous utilisez une expression d’un autre type dans un contexte où une **`void`** expression est requise, sa valeur est ignorée.

Pour se conformer à la spécification ANSI, <strong>void \* \* </strong> ne peut pas être utilisé comme <strong>int \* \* </strong>. Seul **`void`** <strong>\*</strong> peut être utilisé comme pointeur vers un type non spécifié.

**FIN spécifique à Microsoft**

Vous pouvez créer des spécificateurs de type supplémentaires avec des **`typedef`** déclarations, comme décrit dans [déclarations typedef](../c-language/typedef-declarations.md). Pour plus d'informations sur la taille de chaque type, consultez [Stockage des types de base](../c-language/storage-of-basic-types.md).

## <a name="see-also"></a>Voir aussi

[Déclarations et types](../c-language/declarations-and-types.md)
