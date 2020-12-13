---
description: 'En savoir plus sur : syntaxe de nom de fichier CL'
title: Syntaxe de nom de fichier CL
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
ms.openlocfilehash: c7a657b54f69e2cdc0a126c55bb4102589a84290
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182439"
---
# <a name="cl-filename-syntax"></a>Syntaxe de nom de fichier CL

CL accepte les fichiers dont les noms respectent les conventions d'affectation de noms FAT, HPFS ou NTFS. Un nom de fichier peut inclure un chemin d’accès complet ou partiel. Un chemin d’accès complet comprend un nom de lecteur et un ou plusieurs noms de répertoire. CL accepte les noms de fichiers séparés par des barres obliques inverses ( \\ ) ou des barres obliques (/). Les noms de fichiers qui contiennent des espaces doivent être mis entre guillemets doubles. Un chemin d’accès partiel omet le nom de lecteur, CL considérant qu’il s’agit du lecteur actif. Si vous ne spécifiez pas de chemin d’accès, CL considère que le fichier se trouve dans le répertoire actif.

L’extension de nom de fichier détermine la façon dont les fichiers sont traités. Les fichiers C et C++, qui ont l'extension .c, .cxx ou .cpp, sont compilés. Les autres fichiers, notamment les fichiers .obj, les bibliothèques (.lib) et les fichiers de définition de module (.def), sont passés à l'éditeur de liens sans avoir été traités.

## <a name="see-also"></a>Voir aussi

[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
