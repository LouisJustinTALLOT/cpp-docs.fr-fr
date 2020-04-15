---
title: Prise en charge MBCS dans Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- tools [C++], MBCS support
- Asian languages [C++]
- Code Editor [C++], MBCS support
- IME [C++]
- Chinese characters [C++]
- Input Method Editor [C++], MBCS
- resource editors [C++], MBCS support
- debugger [C++], MBCS support
- character sets [C++], multibyte
- Japanese characters [C++]
- multibyte characters [C++]
- Kanji character support [C++]
- NMAKE program, MBCS support
- double-byte character sets [C++]
- IME [C++], MBCS
- Input Method Editor [C++]
- MBCS [C++], enabling
ms.assetid: 6179f6b7-bc61-4a48-9267-fb7951223e38
ms.openlocfilehash: 404fcee5e48d8db28e56a005f24f8cac5892240e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375790"
---
# <a name="mbcs-support-in-visual-c"></a>Prise en charge MBCS dans Visual C++

Lorsqu’il est exécuté sur une version MBCS de Windows, le système de développement Visual CMD (y compris l’éditeur de code source intégré, débbugger et outils de ligne de commande) est activé par MBCS, à l’exception de la fenêtre mémoire.

La fenêtre mémoire n’interprète pas les octets des données comme des caractères MBCS, même si elle peut les interpréter comme des caractères ANSI ou Unicode. Les caractères ANSI sont toujours 1 octet dans la taille et les caractères Unicode sont 2 octets de taille. Avec MBCS, les caractères peuvent être de 1 ou 2 octets de taille et leur interprétation dépend de la page de code qui est utilisée. Pour cette raison, il est difficile pour la fenêtre de mémoire d’afficher de façon fiable les caractères MBCS. La fenêtre de mémoire ne peut pas savoir quel byte est le début d’un personnage. Le développeur peut afficher les valeurs d’ente dans la fenêtre de mémoire et rechercher la valeur dans les tables pour déterminer la représentation des personnages. Cela est possible parce que le développeur connaît l’adresse de départ d’une chaîne basée sur le code source.

Visual CMD accepte les caractères doubles-byte partout où il est approprié de le faire. Cela comprend les noms de chemin et de fichiers dans les boîtes de dialogue et les entrées de texte dans l’éditeur de ressources Visual CMD (par exemple, le texte statique dans l’éditeur de dialogue et les entrées de texte statique dans l’éditeur d’icônes). De plus, le préprocesseur reconnaît certaines directives à double `#include` pareil — par `code_seg` `data_seg` exemple, les noms de fichiers dans les déclarations et les arguments à l’intention et les pragmas. Dans l’éditeur de code source, les caractères double-byte dans les commentaires et les littérals de chaîne sont acceptés, bien que pas dans les éléments de langue C/CMD (tels que les noms variables).

## <a name="support-for-the-input-method-editor-ime"></a><a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Soutien à l’éditeur de la méthode d’entrée (IME)

Les applications écrites pour les marchés d’Asie de l’Est qui utilisent MBCS (par exemple, le Japon) prennent normalement en charge l’IME Windows pour entrer des caractères à la fois un seul et double-byte. L’environnement de développement Visual CMD contient un soutien complet pour l’IME.

Les claviers japonais ne prennent pas directement en charge les personnages kanji. L’IME convertit une chaîne phonétique, entrée dans l’un des autres alphabets japonais (Romaji, Katakana ou Hiragana) en ses représentations Kanji possibles. S’il y a ambiguïté, vous pouvez choisir parmi plusieurs alternatives. Lorsque vous avez sélectionné le personnage Kanji `WM_CHAR` prévu, l’IME transmet deux messages à l’application de contrôle.

L’IME, activé par\` la combinaison de clés ALTMD, apparaît sous forme d’un ensemble de boutons (un indicateur) et d’une fenêtre de conversion. L’application positionne la fenêtre au point d’insertion du texte. L’application `WM_MOVE` doit `WM_SIZE` manipuler et messages en repositionnant la fenêtre de conversion pour se conformer au nouvel emplacement ou taille de la fenêtre cible.

Si vous voulez que les utilisateurs de votre application aient la possibilité d’entrer des caractères Kanji, l’application doit gérer les messages IME Windows. Pour plus d’informations sur la programmation IME, voir [Input Method Manager](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Visuel CMD Debugger

Le débbugger Visual CMD offre la possibilité de définir des points d’arrêt sur les messages IME. En outre, la fenêtre Mémoire peut afficher des caractères double-byte.

## <a name="command-line-tools"></a>Outils en ligne de commande

Les outils de la ligne de commande Visual CMD, y compris le compilateur, NMAKE et le compilateur de ressources (RC. EXE), sont compatibles MBCS. Vous pouvez utiliser l’option compilateur/c du compilateur de ressources pour modifier la page de code par défaut lors de la compilation des ressources de votre application.

Pour modifier le local par défaut au temps de compilation du code source, utilisez [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Outils graphiques

Les outils Windows Visual CMD, tels que SpyMD et les outils d’édition de ressources, prennent pleinement en charge les chaînes IME.

## <a name="see-also"></a>Voir aussi

[Prise en charge des ensembles de personnages multioctets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)
