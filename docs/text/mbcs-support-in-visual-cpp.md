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
ms.openlocfilehash: b5f2b6dd56d3a755ee73058c024152e12157a6bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501943"
---
# <a name="mbcs-support-in-visual-c"></a>Prise en charge MBCS dans Visual C++

Lorsqu’il est exécuté sur une version MBCS de Windows, le système C++ de développement visuel (y compris l’éditeur de code source intégré, le débogueur et les outils en ligne de commande) est compatible MBCS, à l’exception de la fenêtre mémoire.

La fenêtre mémoire n’interprète pas les octets de données comme des caractères MBCS, même s’ils peuvent les interpréter comme des caractères ANSI ou Unicode. Les caractères ANSI ont toujours une taille de 1 octet et les caractères Unicode ont une taille de 2 octets. Avec MBCS, les caractères peuvent avoir une taille de 1 ou 2 octets et leur interprétation dépend de la page de codes en cours d’utilisation. Pour cette raison, il est difficile pour la fenêtre de mémoire d’afficher de manière fiable des caractères MBCS. La fenêtre mémoire ne peut pas savoir quel octet est le début d’un caractère. Le développeur peut afficher les valeurs d’octets dans la fenêtre mémoire et rechercher la valeur dans les tables pour déterminer la représentation de caractère. Cela est possible car le développeur connaît l’adresse de départ d’une chaîne basée sur le code source.

Visual C++ accepte les caractères codés sur deux octets, quel que soit l’endroit où il est approprié. Cela comprend les noms de chemin d’accès et les noms de fichiers dans les boîtes C++ de dialogue et les entrées de texte dans l’éditeur de ressources visuel (par exemple, le texte statique de l’éditeur de boîtes de dialogue et les entrées de texte statiques dans l’éditeur d’icônes). En outre, le préprocesseur reconnaît certaines directives sur deux octets, par exemple, les noms de fichiers `#include` dans les instructions et comme arguments pour `code_seg` les `data_seg` pragmas et. Dans l’éditeur de code source, les caractères codés sur deux octets dans les commentaires et les littéraux de chaîne sontC++ acceptés, bien qu’ils ne soient pas dans les éléments C/Language (tels que les noms de variables).

##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a>Prise en charge de l’éditeur de méthode d’entrée (IME)

Les applications écrites pour les marchés de l’Asie de l’est qui utilisent MBCS (par exemple, le Japon) prennent normalement en charge l’IME Windows pour la saisie de caractères codés sur un ou deux octets. L’environnement C++ de développement visuel contient une prise en charge complète de l’IME.

Les claviers japonais ne prennent pas directement en charge les caractères Kanji. L’IME convertit une chaîne phonétique, entrée dans l’un des autres alphabets japonais (romaji, katakana ou Hiragana) en ses représentations kanji possibles. En cas d’ambiguïté, vous pouvez choisir parmi plusieurs alternatives. Quand vous avez sélectionné le caractère Kanji prévu, l’IME transmet deux `WM_CHAR` messages à l’application de contrôle.

L’IME, activé par la combinaison de\` touches Alt +, s’affiche sous la forme d’un ensemble de boutons (un indicateur) et d’une fenêtre de conversion. L’application positionne la fenêtre au niveau du point d’insertion de texte. L’application doit gérer `WM_MOVE` les `WM_SIZE` messages et en repositionnant la fenêtre de conversion pour qu’elle soit conforme au nouvel emplacement ou à la nouvelle taille de la fenêtre cible.

Si vous souhaitez que les utilisateurs de votre application aient la possibilité d’entrer des caractères Kanji, l’application doit gérer les messages IME Windows. Pour plus d’informations sur la programmation IME, consultez [Gestionnaire de méthode d’entrée](/windows/win32/intl/input-method-manager).

## <a name="visual-c-debugger"></a>Débogueur visuel C++

Le débogueur visuel C++ permet de définir des points d’arrêt sur les messages IME. En outre, la fenêtre mémoire peut afficher des caractères codés sur deux octets.

## <a name="command-line-tools"></a>Outils en ligne de commande

Les outils C++ en ligne de commande visuels, y compris le compilateur, NMAKE et le compilateur de ressources (RC. EXE), sont compatibles MBCS. Vous pouvez utiliser l’option/c du compilateur de ressources pour modifier la page de codes par défaut lors de la compilation des ressources de votre application.

Pour modifier les paramètres régionaux par défaut au moment de la compilation du code source, utilisez [#pragma setlocale](../preprocessor/setlocale.md).

## <a name="graphical-tools"></a>Outils graphiques

Les outils C++ visuels basés sur Windows, tels que Spy + + et les outils d’édition de ressources, prennent entièrement en charge les chaînes IME.

## <a name="see-also"></a>Voir aussi

[Prise en charge des jeux de caractères multioctets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)
