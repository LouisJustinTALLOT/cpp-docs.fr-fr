---
title: Jeux de caractères
ms.date: 04/12/2018
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 5282d5b227e71c0ba6f822a9534a8a31cbd86db9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664631"
---
# <a name="character-sets"></a>Jeux de caractères

Le texte d’un programme C++ est stocké dans des fichiers sources qui utilisent un encodage des caractères particulier. La norme C++ spécifie un jeu de caractères sources de base pour les fichiers sources, et un jeu de caractères d’exécution de base pour les fichiers compilés. Visual C++ permet l’utilisation d’un jeu supplémentaire de caractères spécifiques à des paramètres régionaux dans les fichiers sources et les fichiers compilés.

## <a name="character-sets"></a>Jeux de caractères

La norme C++ spécifie un *jeu de caractères sources de base* qui peut être utilisé dans les fichiers sources. Pour représenter des caractères qui ne font pas partie de ce jeu, des caractères supplémentaires peuvent être spécifiés à l’aide d’un *nom de caractère universel*. Quand ils sont compilés, le *jeu de caractères d’exécution de base* et le *jeu de caractères larges d’exécution de base* représentent les caractères et les chaînes qui peuvent apparaître dans un programme. L’implémentation de Visual C++ autorise des caractères supplémentaires dans le code source et dans le code compilé.

### <a name="basic-source-character-set"></a>Jeu de caractères sources de base

Le *jeu de caractères sources de base* est constitué de 96 caractères qui peuvent être utilisés dans les fichiers sources. Ce jeu comprend le caractère d’espace, la tabulation horizontale, la tabulation verticale, les caractères de contrôle de saut de page et de nouvelle ligne, ainsi que cet ensemble de caractères graphiques :

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Section spécifique à Microsoft**

Visual C++ inclut le caractère `$` comme membre du jeu de caractères sources de base. Visual C++ permet aussi l’utilisation d’un jeu supplémentaire de caractères dans les fichiers sources, en fonction de l’encodage du fichier. Par défaut, Visual Studio stocke les fichiers sources en utilisant la page de codes par défaut. Quand des fichiers sources sont enregistrés en utilisant une page de codes spécifique à des paramètres régionaux ou une page de codes Unicode, Visual C++ vous permet d’utiliser tous les caractères de cette page de codes dans votre code source, excepté pour les codes de contrôle qui ne sont pas explicitement autorisés dans le jeu de caractères sources de base. Par exemple, vous pouvez placer des caractères du japonais dans les commentaires, les identificateurs ou les littéraux de chaîne si vous enregistrez le fichier en utilisant une page de codes du japonais. Visual C++  n’autorise pas les séquences de caractères qui ne peuvent pas être traduites en caractères multioctets valides ou en points de code Unicode. Selon les options du compilateur, certains caractères autorisés ne peuvent pas apparaître dans les identificateurs. Pour plus d’informations, consultez [Identifiers](../cpp/identifiers-cpp.md).

**FIN de la section spécifique à Microsoft**

### <a name="universal-character-names"></a>noms de caractères universels

Comme les programmes C++ peuvent utiliser bien plus de caractères que ceux qui sont spécifiés dans le jeu de caractères sources de base, vous pouvez spécifier ces caractères d’une façon portable en utilisant des *noms de caractères universels*. Un nom de caractère universel est constitué d’une séquence de caractères qui représentent un point de code Unicode.  Celles-ci peuvent prendre deux formes. Utilisez `\UNNNNNNNN` pour représenter un point de code Unicode de la forme U+NNNNNNNN, où NNNNNNNN est le numéro du point de code hexadécimal sur huit chiffres. Utilisez la séquence de quatre chiffres `\uNNNN` pour représenter un point de code Unicode de la forme U+0000NNNN.

Les noms de caractères universels peuvent être utilisés dans les identificateurs, et dans les littéraux de chaînes et de caractères. Un nom de caractère universel ne peut pas être utilisé pour représenter un point de code de substitution dans la plage 0xD800-0xDFFF. Au lieu de cela, utilisez le point de code souhaité : le compilateur génère automatiquement les caractères de substitution requis. D’autres restrictions s’appliquent aux noms de caractères universels qui peuvent être utilisés dans les identificateurs. Pour plus d’informations, consultez [Identifiers](../cpp/identifiers-cpp.md) et [String and Character Literals](../cpp/string-and-character-literals-cpp.md).

**Section spécifique à Microsoft**

Le compilateur Visual C++ traite de façon interchangeable un caractère sous forme de nom de caractère universel et sous forme de littéral. Par exemple, vous pouvez déclarer un identificateur en utilisant la forme de nom de caractère universel et l’utiliser sous forme de littéral :

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Le format des caractères étendus sur le Presse-papiers Windows est spécifique aux valeurs des paramètres régionaux de l’application. Le fait de couper et de coller ces caractères dans votre code depuis une autre application peut introduire des encodages de caractères inattendus. Ceci peut aboutir à des erreurs d’analyse sans cause visible dans votre code. Nous vous recommandons de définir l’encodage de vos fichiers sources sur une page de codes Unicode avant de coller des caractères étendus. Nous vous recommandons aussi d’utiliser un éditeur de méthode d’entrée (IME) ou l’application Character Map pour générer des caractères étendus.

**FIN de la section spécifique à Microsoft**

### <a name="basic-execution-character-set"></a>jeu de caractères d’exécution de base

Le *jeu de caractères d’exécution de base* et le *jeu de caractères larges d’exécution de base* sont constitués de tous les caractères du jeu de caractères sources de base, et des caractères de contrôle qui représentent le caractère alerte, barre oblique inverse, retour chariot et null. Le *jeu de caractères d’exécution* et le *jeu de caractères larges d’exécution* sont des sur-ensembles des jeux de base. Ils comprennent des caractères sources définis par une implémentation en dehors du jeu de caractères sources de base. Le jeu de caractères d’exécution a une représentation spécifique aux paramètres régionaux.