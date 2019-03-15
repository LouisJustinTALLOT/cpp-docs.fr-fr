---
title: Sortie LINK
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 183f83501d930188032ec4209623ef7cf1a30efa
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807622"
---
# <a name="link-output"></a>Sortie LINK

Sortie LINK inclut des fichiers .exe, DLL, fichiers de mappage et les messages.

##  <a name="_core_output_files"></a> Fichiers de sortie

Le fichier de sortie par défaut à partir du lien est un fichier .exe. Si le [/DLL](dll-build-a-dll.md) est spécifiée, LINK génère un fichier .dll. Vous pouvez contrôler le nom de fichier de sortie avec la [nom de fichier de sortie (/ OUT)](out-output-file-name.md) option.

En mode incrémentiel, LINK crée un fichier .ilk pour conserver les informations d’état pour les générations incrémentielles ultérieures du programme. Pour plus d’informations sur les fichiers .ilk, consultez [fichiers .ilk](dot-ilk-files-as-linker-input.md). Pour plus d’informations sur la liaison incrémentielle, consultez le [lier par incrément (/ INCREMENTAL)](incremental-link-incrementally.md) option.

Quand LINK crée un programme qui contienne des exportations (généralement une DLL), il génère également un fichier .lib, sauf si un fichier .exp a été utilisé dans la build. Vous pouvez contrôler le nom de fichier de bibliothèque importation avec la [/IMPLIB](implib-name-import-library.md) option.

Si le [générer fichier de mappage (/Map)](map-generate-mapfile.md) est spécifiée, LINK crée un fichier de mappage.

Si le [générer des infos de débogage (/Debug)](debug-generate-debug-info.md) est spécifiée, LINK crée un fichier PDB pour contenir les informations de débogage pour le programme.

##  <a name="_core_other_output"></a> Autre sortie

Quand vous tapez `link` sans aucune autre entrée de ligne de commande, le lien affiche une instruction d’utilisation qui récapitule ses options.

LIEN affiche un message de copyright et la version et répercute la commande-fichier d’entrée, à moins que le [supprimer la bannière de démarrage (/ NOLOGO)](nologo-suppress-startup-banner-linker.md) option est utilisée.

Vous pouvez utiliser la [imprimer les Messages d’avancement (/verbose)](verbose-print-progress-messages.md) option pour afficher des détails supplémentaires sur la build.

LIEN émet des messages d’erreur et d’avertissement sous la forme LNK*nnnn*. Ce préfixe de l’erreur et de la plage de numéros sont également utilisés par LIB, DUMPBIN et EDITBIN.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
