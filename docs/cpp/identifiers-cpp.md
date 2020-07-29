---
title: Identificateurs (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- decorated names
- decorated names, about decorated names
- identifiers, C++
- white space, in C++ identifiers
- identifiers [C++]
ms.assetid: 03a0dfb1-4530-4cdf-8295-5ea4dca4c1b8
ms.openlocfilehash: 2d16dd318cd42b6294ef60edf44a16ccaf47b99b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87187671"
---
# <a name="identifiers-c"></a>Identificateurs (C++)

Un identificateur est une séquence de caractères servant à désigner l'un des éléments suivants :

- Nom d'objet ou de variable

- Nom de classe, de structure ou d'union

- Nom de type énuméré

- Membre d'une classe, d'une structure, d'une union ou d'une énumération

- Fonction ou fonction membre de classe

- Nom de typedef

- Nom d'étiquette

- Nom de macro

- Paramètre de macro

Les caractères suivants sont autorisés dans un identificateur :

```
_ a b c d e f g h i j k l m
n o p q r s t u v w x y z
A B C D E F G H I J K L M
N O P Q R S T U V W X Y Z
```

Certaines plages de noms de caractères universels sont également autorisées dans un identificateur.  Un nom de caractère universel dans un identificateur ne peut pas désigner un caractère de contrôle ou un caractère du jeu de caractères sources de base. Pour plus d'informations, consultez [Character Sets](../cpp/character-sets.md). Ces plages de nombres de point de code Unicode sont autorisées en tant que noms de caractères universels pour n’importe quel caractère d’un identificateur :

- 00A8, 00AA, 00AD, 00AF, 00B2-00B5, 00B7-00BA, 00BC-00BE, 00C0-00D6, 00D8-00F6, 00F8-00FF, 0100-02FF, 0370-167F, 1681-180D, 180F-1DBF, 1E00-1FFF, 200B-200D, 202A-202E, 203F-2040, 2054, 2060-206F, 2070-20CF, 2100-218F, 2460-24FF, 2776-2793, 2C00-2DFF, 2E80-2FFF, 3004-3007, 3021-302F, 3031-303F, 3040-D7FF, F900-FD3D, FD40-FDCF, FDF0-FE1F, FE30-FE44, FE47-FFFD, 10000-1FFFD, 20000-2FFFD, 30000-3FFFD, 40000-4FFFD, 50000-5FFFD, 60000-6FFFD, 70000-7FFFD, 80000-8FFFD, 90000-9FFFD, A0000-AFFFD, B0000-BFFFD, C0000-CFFFD, D0000-DFFFD, E0000-EFFFD

Les caractères suivants sont autorisés comme caractères quelconques d’un identificateur, à l’exception du premier caractère :

```
0 1 2 3 4 5 6 7 8 9
```

Ces plages de nombres de point de code Unicode sont également autorisées en tant que noms de caractères universels pour n’importe quel caractère d’un identificateur, à l’exception du premier :

- 0300-036F, 1DC0-1DFF, 20D0-20FF, FE20-FE2F

**Spécifique à Microsoft**

Seuls les 2 048 premiers caractères des identificateurs Microsoft C++ sont significatifs. Les noms des types définis par l'utilisateur sont « décorés » par le compilateur de manière à conserver les informations de type. Le nom résultant, qui inclut les informations de type, ne peut pas comporter plus de 2 048 caractères. (Pour plus d’informations, consultez [noms décorés](../build/reference/decorated-names.md) .) Les facteurs qui peuvent influencer la longueur d’un identificateur décoré sont les suivants :

- Si l'identificateur désigne ou non un objet de type défini par l'utilisateur ou un type dérivé d'un type défini par l'utilisateur.

- Si l'identificateur désigne ou non une fonction ou un type dérivé d'une fonction.

- Le nombre d'arguments d'une fonction.

Le signe dollar `$` est un caractère d’identificateur valide dans le compilateur Microsoft C++ (MSVC). MSVC vous permet également d’utiliser les caractères réels représentés par les plages autorisées de noms de caractères universels dans les identificateurs. Pour utiliser ces caractères, vous devez enregistrer le fichier à l’aide d’une page de codes d’encodage de fichier qui les inclut.  Cet exemple montre comment utiliser les caractères étendus et les noms de caractères universels de manière interchangeable dans votre code.

```cpp
// extended_identifier.cpp
// In Visual Studio, use File, Advanced Save Options to set
// the file encoding to Unicode codepage 1200
struct テスト         // Japanese 'test'
{
    void トスト() {}  // Japanese 'toast'
};

int main() {
    テスト \u30D1\u30F3;  // Japanese パン 'bread' in UCN form
    パン.トスト();        // compiler recognizes UCN or literal form
}
```

La plage des caractères autorisés dans un identificateur est moins restrictive durant la compilation du code C++/CLI. Les identificateurs contenus dans du code compilé à l’aide de /clr doivent suivre la  [norme ECMA-335 : Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

**FIN spécifique à Microsoft**

Le premier caractère d'un identificateur doit être un caractère alphabétique, majuscule ou minuscule, ou un trait de soulignement ( **_** ). Comme les identificateurs C++ respectent la casse, `fileName` est différent de `FileName`.

Les identificateurs ne peuvent pas avoir exactement la même orthographe et la même casse que les mots clés. Les identificateurs contenant des mots clés sont autorisés. Par exemple, `Pint` est un identificateur légal, même s’il contient **`int`** , qui est un mot clé.

L’utilisation de deux traits de soulignement ( **_ _** ) séquentiels dans un identificateur, ou d’un seul trait de soulignement suivi d’une lettre majuscule, est réservée aux implémentations C++ dans toutes les portées. Évitez d'utiliser un seul trait de soulignement de début suivi d'une lettre minuscule pour les noms avec une portée de fichier en raison de conflits possibles avec les identificateurs réservés actuels ou futurs.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)
