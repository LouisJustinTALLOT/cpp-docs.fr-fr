---
description: 'En savoir plus sur : jetons et jeux de caractères'
title: Jetons et jeux de caractères
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: b5a6868f5e4c01772758acaa0e44459e72b16a84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308469"
---
# <a name="tokens-and-character-sets"></a>Jetons et jeux de caractères

Le texte d’un programme C++ se compose de jetons et d' *espaces blancs*. Un jeton est le plus petit élément d’un programme C++ qui est significatif pour le compilateur. L’analyseur C++ reconnaît ces types de jetons :

- [Mots clés](../cpp/keywords-cpp.md)
- [Identificateurs](../cpp/identifiers-cpp.md)
- [Littéraux numériques, booléens et de pointeur](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [Littéraux de chaîne et de caractère](../cpp/string-and-character-literals-cpp.md)
- [Littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md)
- [Opérateurs](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [Signes de ponctuation](../cpp/punctuators-cpp.md)

Les jetons sont généralement séparés par un *espace blanc*, qui peut être un ou plusieurs des éléments suivants :

- Espaces
- Tabulations horizontales ou verticales
- Nouvelles lignes
- Flux de formulaire
- Commentaires

## <a name="basic-source-character-set"></a>Jeu de caractères sources de base

La norme C++ spécifie un *jeu de caractères sources de base* qui peut être utilisé dans les fichiers sources. Pour représenter des caractères qui ne font pas partie de ce jeu, des caractères supplémentaires peuvent être spécifiés à l’aide d’un *nom de caractère universel*. L’implémentation MSVC autorise des caractères supplémentaires. Le *jeu de caractères source de base* se compose de 96 caractères qui peuvent être utilisés dans les fichiers sources. Ce jeu comprend le caractère d’espace, la tabulation horizontale, la tabulation verticale, les caractères de contrôle de saut de page et de nouvelle ligne, ainsi que cet ensemble de caractères graphiques :

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Spécifique à Microsoft**

MSVC comprend le `$` caractère comme membre du jeu de caractères sources de base. MSVC autorise également l’utilisation d’un jeu de caractères supplémentaire dans les fichiers sources, en fonction de l’encodage du fichier. Par défaut, Visual Studio stocke les fichiers sources en utilisant la page de codes par défaut. Quand des fichiers sources sont enregistrés à l’aide d’une page de codes spécifique aux paramètres régionaux ou d’une page de codes Unicode, MSVC vous permet d’utiliser l’un des caractères de cette page de codes dans votre code source, à l’exception des codes de contrôle qui ne sont pas explicitement autorisés dans le jeu de caractères source de base. Par exemple, vous pouvez placer des caractères du japonais dans les commentaires, les identificateurs ou les littéraux de chaîne si vous enregistrez le fichier en utilisant une page de codes du japonais. MSVC n’autorise pas les séquences de caractères qui ne peuvent pas être traduites en caractères multioctets valides ou en points de code Unicode. Selon les options du compilateur, certains caractères autorisés ne peuvent pas apparaître dans les identificateurs. Pour plus d’informations, consultez [Identificateurs](../cpp/identifiers-cpp.md).

**FIN spécifique à Microsoft**

### <a name="universal-character-names"></a>noms de caractères universels

Comme les programmes C++ peuvent utiliser bien plus de caractères que ceux qui sont spécifiés dans le jeu de caractères sources de base, vous pouvez spécifier ces caractères d’une façon portable en utilisant des *noms de caractères universels*. Un nom de caractère universel est constitué d’une séquence de caractères qui représentent un point de code Unicode.  Celles-ci peuvent prendre deux formes. Utilisez `\UNNNNNNNN` pour représenter un point de code Unicode de la forme U+NNNNNNNN, où NNNNNNNN est le numéro du point de code hexadécimal sur huit chiffres. Utilisez la séquence de quatre chiffres `\uNNNN` pour représenter un point de code Unicode de la forme U+0000NNNN.

Les noms de caractères universels peuvent être utilisés dans les identificateurs, et dans les littéraux de chaînes et de caractères. Un nom de caractère universel ne peut pas être utilisé pour représenter un point de code de substitution dans la plage 0xD800-0xDFFF. Au lieu de cela, utilisez le point de code souhaité : le compilateur génère automatiquement les caractères de substitution requis. D’autres restrictions s’appliquent aux noms de caractères universels qui peuvent être utilisés dans les identificateurs. Pour plus d’informations, consultez [Identifiers](../cpp/identifiers-cpp.md) et [String and Character Literals](../cpp/string-and-character-literals-cpp.md).

**Spécifique à Microsoft**

Le compilateur Microsoft C++ traite de façon interchangeable un caractère sous forme de nom de caractère universel et sous forme de littéral. Par exemple, vous pouvez déclarer un identificateur en utilisant la forme de nom de caractère universel et l’utiliser sous forme de littéral :

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Le format des caractères étendus sur le Presse-papiers Windows est spécifique aux valeurs des paramètres régionaux de l’application. Le fait de couper et de coller ces caractères dans votre code depuis une autre application peut introduire des encodages de caractères inattendus. Ceci peut aboutir à des erreurs d’analyse sans cause visible dans votre code. Nous vous recommandons de définir l’encodage de vos fichiers sources sur une page de codes Unicode avant de coller des caractères étendus. Nous vous recommandons aussi d’utiliser un éditeur de méthode d’entrée (IME) ou l’application Character Map pour générer des caractères étendus.

**FIN spécifique à Microsoft**

### <a name="execution-character-sets"></a>Jeux de caractères d’exécution

Les *jeux de caractères d’exécution* représentent les caractères et les chaînes qui peuvent apparaître dans un programme compilé. Ces jeux de caractères sont constitués de tous les caractères autorisés dans un fichier source, ainsi que des caractères de contrôle qui représentent l’alerte, le retour arrière, le retour chariot et le caractère null. Le jeu de caractères d’exécution a une représentation spécifique aux paramètres régionaux.
