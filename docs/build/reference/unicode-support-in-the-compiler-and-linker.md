---
title: Prise en charge Unicode dans le compilateur et l'éditeur de liens
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: cb21165e51960c0ca2f728381413c1a7260c9f83
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494976"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Prise en charge Unicode dans le compilateur et l'éditeur de liens

La plupart des outils de génération Visual C++ prend en charge Unicode entrées et sorties.

## <a name="filenames"></a>Noms de fichiers

Noms de fichiers spécifiés sur la ligne de commande ou dans les directives du compilateur (tel que `#include`) peut contenir des caractères Unicode.

## <a name="source-code-files"></a>Fichiers de code source

Les caractères Unicode sont pris en charge dans les identificateurs, les macros, les littéraux de chaîne et de caractère et dans des commentaires.  Noms de caractères universels sont également pris en charge.

Unicode peuvent être entré dans un fichier de code source dans les encodages suivants :

- UTF-16 little endian avec ou sans marque d’ordre d’octet (BOM)

- UTF-16 big endian avec ou sans BOM

- UTF-8 avec BOM

## <a name="output"></a>Sortie

Pendant la compilation, le compilateur génère des diagnostics sur la console au format UTF-16.  Les caractères qui peuvent être affichés sur votre console dépendent des propriétés de la fenêtre de console.  Il est redirigé vers un fichier de sortie du compilateur dans la page de codes de console ANSI actuelle.

## <a name="linker-response-files-and-def-files"></a>Fichiers de réponse de l’éditeur de liens et. Fichiers DEF

Fichiers réponse et fichiers DEF peuvent être soit UTF-16 avec une marque BOM ou ANSI.

## <a name="asm-and-cod-dumps"></a>dumps .asm et .cod

dumps .asm et .cod est au format ANSI par défaut pour la compatibilité avec MASM. Utilisez [/FAu](../../build/reference/fa-fa-listing-file.md) en sortie UTF-8. Notez que si vous spécifiez **/FAS**, la source par recoupement sera directement affichée et peut sembler altérée, par exemple, si vous n’avez pas spécifié et que le code source est UTF-8 **/FAsu**.

## <a name="see-also"></a>Voir aussi

[Générer du code C/C++ sur la ligne de commande](../../build/building-on-the-command-line.md)