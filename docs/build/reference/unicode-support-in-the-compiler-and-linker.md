---
description: 'En savoir plus sur : prise en charge d’Unicode dans le compilateur et l’éditeur de liens'
title: Prise en charge Unicode dans le compilateur et l'éditeur de liens
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: c853907dd0d70a4ab7311c41f51d8d73bb25cf20
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178951"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Prise en charge Unicode dans le compilateur et l'éditeur de liens

La plupart des Visual C++ outils de génération prennent en charge les entrées et sorties Unicode.

## <a name="filenames"></a>Noms de fichiers

Les noms de fichiers spécifiés sur la ligne de commande ou dans les directives de compilateur (tels que `#include` ) peuvent contenir des caractères Unicode.

## <a name="source-code-files"></a>Fichiers de code source

Les caractères Unicode sont pris en charge dans les identificateurs, les macros, les littéraux de chaîne et de caractère et dans les commentaires.  Les noms de caractères universels sont également pris en charge.

Unicode peut être entré dans un fichier de code source dans les encodages suivants :

- UTF-16 Little endian avec ou sans marque d’ordre d’octet (BOM)

- UTF-16 Big endian avec ou sans BOM

- UTF-8 with BOM

## <a name="output"></a>Output

Pendant la compilation, le compilateur génère des diagnostics sur la console en UTF-16.  Les caractères qui peuvent être affichés sur votre console dépendent des propriétés de la fenêtre de console.  La sortie de compilateur redirigée vers un fichier se trouve dans la page de codes de la console ANSI actuelle.

## <a name="linker-response-files-and-def-files"></a>Fichiers réponse de l’éditeur de liens et. Fichiers DEF

Les fichiers réponse et les fichiers DEF peuvent être au format UTF-16 avec une marque de nomenclature ou ANSI.

## <a name="asm-and-cod-dumps"></a>Dumps. asm et. COD

les dumps. asm et. COD sont par défaut en ANSI pour des compatibilités avec MASM. Utilisez [/FAu](fa-fa-listing-file.md) pour la sortie UTF-8. Notez que si vous spécifiez **/FAS**, la source mélangée est directement imprimée et peut paraître tronquée, par exemple si le code source est UTF-8 et que vous n’avez pas spécifié **/fasu**.

## <a name="see-also"></a>Voir aussi

[Utiliser l’ensemble d’outils MSVC à partir de la ligne de commande](../building-on-the-command-line.md)
