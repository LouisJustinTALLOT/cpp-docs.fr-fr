---
title: Prise en charge MBCS dans Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 51472ba9c0bc15d6b12ddcd3a3b88b65a3a2682b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205194"
---
# <a name="mbcs-support-in-visual-c"></a>Prise en charge MBCS dans Visual C++
Lorsque vous exécutez une version prenant en charge MBCS de Windows, le système de développement Visual C++ (y compris les outils de ligne de commande, éditeur et débogueur de code source intégré) est MBCS, à l’exception de la fenêtre de la mémoire.  
  
 La fenêtre de mémoire n’interprète pas les octets de données en tant que caractères MBCS, même si elle peut les interpréter comme des caractères ANSI ou Unicode. Les caractères ANSI sont toujours 1 octet dans la taille et les caractères Unicode sont de taille de 2 octets. Avec MBCS, les caractères peuvent être de taille de 1 ou 2 octets et leur interprétation dépend de la page de codes est en cours d’utilisation. Pour cette raison, il est difficile pour la fenêtre de la mémoire pour afficher des caractères MBCS de manière fiable. La fenêtre mémoire ne peut pas savoir quel octet correspond au début d’un caractère. Le développeur peut afficher les valeurs d’octets dans la fenêtre de la mémoire et rechercher la valeur dans les tables pour déterminer la représentation sous forme de caractère. Cela est possible car le développeur sait que l’adresse de départ d’une chaîne basée sur le code source.  
  
 Visual C++ accepte les caractères codés sur deux partout où il convient de le faire. Cela inclut les noms de chemin d’accès et noms de fichiers dans les boîtes de dialogue et les entrées de texte dans l’éditeur de ressources Visual C++ (par exemple, un texte statique dans l’éditeur de boîtes de dialogue) et les entrées de texte statique dans l’éditeur d’icônes. En outre, le préprocesseur reconnaît certaines directives sur deux octets, par exemple, noms de fichiers dans `#include` instructions et en tant qu’arguments à la `code_seg` et `data_seg` pragmas. Dans l’éditeur de code source, des caractères codés dans les commentaires et les littéraux de chaîne sont acceptés, mais pas dans les éléments de langage C/C++ (par exemple, les noms de variables).  
  
##  <a name="_core_support_for_the_input_method_editor_.28.ime.29"></a> Prise en charge pour l’éditeur de méthode d’entrée (IME)  
 Applications écrites pour Extrême-Orient marchés qui utilisent MBCS (par exemple, le Japon) normalement prise en charge l’IME Windows permettant d’entrer les deux caractères d’octet et double. L’environnement de développement Visual C++ contient une prise en charge complète pour l’IME. Pour plus d’informations, consultez [IME, exemple : montre comment implémenter IME niveau 3 et de contrôle du Mode IME](https://msdn.microsoft.com/87ebdf65-cef0-451d-a6fc-d5fb64178b14).  
  
 Claviers japonais ne prennent pas directement en charge les caractères Kanji. L’IME convertit une chaîne phonétique, entrée dans un des alphabets japonais (romain, Katakana et Hiragana) dans les représentations Kanji possibles. En cas d’ambiguïté, vous pouvez sélectionner parmi plusieurs solutions. Lorsque vous avez sélectionné le caractère Kanji, l’IME passe deux `WM_CHAR` messages à l’application de contrôle.  
  
 L’IME, activé par ALT +\` combinaison de touches, apparaît sous la forme d’un ensemble de boutons (indicateur) et une fenêtre de conversion. L’application positionne la fenêtre au point d’insertion de texte. L’application doit gérer `WM_MOVE` et `WM_SIZE` messages en repositionnant la fenêtre de conversion pour respecter le nouvel emplacement ou la taille de la fenêtre cible.  
  
 Si vous souhaitez que les utilisateurs de votre application d’avoir la possibilité d’entrer des caractères Kanji, l’application doit gérer les messages Windows IME. Pour plus d’informations sur la programmation de l’IME, consultez [éditeur de méthode d’entrée](/previous-versions/windows/desktop/ms776145\(v=vs.85\)).  
  
## <a name="visual-c-debugger"></a>Débogueur Visual C++  
 Le débogueur de Visual C++ fournit la possibilité de définir des points d’arrêt sur les messages IME. En outre, la fenêtre de la mémoire peut afficher des caractères DBCS.  
  
## <a name="command-line-tools"></a>Outils en ligne de commande  
 Les outils de ligne de commande de Visual C++, y compris le compilateur, NMAKE et le compilateur de ressources (RC. (EXE), sont compatibles avec MBCS. Vous pouvez utiliser l’option de /c du compilateur de ressources pour modifier la page de codes par défaut lors de la compilation des ressources de votre application.  
  
 Pour modifier les paramètres régionaux par défaut au moment de compilation de code source, utilisez [#pragma setlocale](../preprocessor/setlocale.md).  
  
## <a name="graphical-tools"></a>Outils graphiques  
 Les outils de Visual C++ Windows, tels que Spy ++ et l’outils d’édition de ressource prennent entièrement en charge les chaînes IME.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge des jeux de caractères multioctets (MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)   
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)