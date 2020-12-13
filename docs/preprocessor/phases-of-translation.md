---
description: 'En savoir plus sur : phases de traduction'
title: Phases de traduction
ms.date: 08/29/2019
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
ms.openlocfilehash: 6a561fe9aa61df293a038a9edfd094dbdef4fe89
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333184"
---
# <a name="phases-of-translation"></a>Phases de traduction

Les programmes C et C++ se composent d'un ou de plusieurs fichiers sources contenant chacun une partie du texte du programme. Un fichier source, ainsi que ses *fichiers include*, les fichiers inclus à l’aide de la `#include` directive de préprocesseur, mais sans inclure les sections de code supprimées par les directives de compilation conditionnelle, telles que `#if` , est appelé une *unité de traduction*.

Les fichiers sources peuvent être traduits à des moments différents. En fait, il est courant de traduire uniquement les fichiers obsolètes. Les unités de traduction traduites peuvent être traitées dans des fichiers objets ou des bibliothèques de codes objet séparés. Ces unités de traduction distinctes et traduites sont ensuite liées pour former un programme exécutable ou une bibliothèque de liens dynamiques (DLL). Pour plus d’informations sur les fichiers qui peuvent être utilisés comme entrée pour l’éditeur de liens, consultez [fichiers d’entrée de lien](../build/reference/link-input-files.md).

Les unités de traduction peuvent communiquer via :

- des appels aux fonctions qui comportent une liaison externe ;

- des appels aux fonctions membres de classe qui comportent une liaison externe ;

- la modification directe d'objets contenant une liaison externe ;

- la modification directe de fichiers ;

- Une communication entre processus (pour les applications Microsoft Windows uniquement).

La liste suivante décrit les phases au cours desquelles le compilateur traduit les fichiers :

*Mappage de caractères*\
Les caractères dans le fichier source sont mappés à la représentation source interne. Les séquences de trigraphe sont converties en représentation interne à un caractère au cours de cette phase.

*Épissure de lignes*\
Toutes les lignes se terminant par une barre oblique inverse ( **\\** ) immédiatement suivie d’un caractère de saut de ligne sont jointes à la ligne suivante dans le fichier source, formant des lignes logiques à partir des lignes physiques. Sauf s’il est vide, un fichier source doit se terminer par un caractère de saut de ligne qui n’est pas précédé d’une barre oblique inverse.

*Jetons*\
Le fichier source est décomposé en jetons de prétraitement et espaces blancs. Chaque commentaire dans le fichier source est remplacé par un espace. Les caractères de saut de ligne sont conservés.

*Prétraitement*\
Les directives de prétraitement sont exécutées et les macros sont développées dans le fichier source. L'instruction `#include` appelle la traduction sur le texte inclus, en commençant par les trois étapes de traduction précédentes.

*Mappage de jeu de caractères*\
Toutes les séquences d'échappement et tous les membres du jeu de caractères de source sont convertis en leur équivalent dans le jeu de caractères d'exécution. Pour Microsoft C et C++, le jeu de caractères source et le jeu de caractères d'exécution sont tous deux au format ASCII.

*Concaténation de chaînes*\
Tous les littéraux de chaîne adjacents et étendus sont concaténés. Par exemple, `"String " "concatenation"` devient `"String concatenation"`.

*Interprétation*\
Tous les jetons sont analysés syntaxiquement et sémantiquement ; ils sont convertis en code objet.

*Liaison*\
Toutes les références externes sont résolues pour créer un programme exécutable ou une bibliothèque de liens dynamiques.

Le compilateur génère des avertissements ou des erreurs lors des phases de traduction dans lesquelles il détecte des erreurs de syntaxe.

L'éditeur de liens résout toutes les références externes et crée un programme exécutable ou une DLL en combinant une ou plusieurs unités de traduction traitées séparément avec les bibliothèques standard.

## <a name="see-also"></a>Voir aussi

[Préprocesseur](../preprocessor/preprocessor.md)
