---
title: Syntaxe de nom de fichier CL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- syntax, compiler filename
- paths, CL compiler filename syntax
- cl.exe compiler, filename syntax
- extensions, specifying to compiler
- file names [C++], CL compiler
- file names [C++]
ms.assetid: 3ca72586-75be-4477-b323-a1be232e80d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 121cd8971be65e15ad6445cb347baf478046bf3e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370460"
---
# <a name="cl-filename-syntax"></a>Syntaxe de nom de fichier CL
CL accepte les fichiers dont les noms respectent les conventions d'affectation de noms FAT, HPFS ou NTFS. Un nom de fichier peut inclure un chemin d'accès complet ou partiel. Un chemin d’accès complet comprend un nom de lecteur et un ou plusieurs noms de répertoire. CL accepte les noms de fichiers séparés par des barres obliques inverses (\\) ou de barres obliques (/). Les noms de fichiers qui contiennent des espaces doivent être mis entre guillemets doubles. Un chemin d'accès partiel omet le nom de lecteur, CL considérant qu'il s'agit du lecteur actif. Si vous ne spécifiez pas de chemin d'accès, CL considère que le fichier se trouve dans le répertoire actif.  
  
 L'extension de nom de fichier détermine la façon dont les fichiers sont traités. Les fichiers C et C++, qui ont l'extension .c, .cxx ou .cpp, sont compilés. Les autres fichiers, notamment les fichiers .obj, les bibliothèques (.lib) et les fichiers de définition de module (.def), sont passés à l'éditeur de liens sans avoir été traités.  
  
## <a name="see-also"></a>Voir aussi  
 [Syntaxe de la ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md)