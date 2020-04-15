---
title: Sortie LINK
ms.date: 11/04/2016
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
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331791"
---
# <a name="link-output"></a>Sortie LINK

La sortie de lien inclut les fichiers .exe, les DLL, les mapfiles et les messages.

## <a name="output-files"></a><a name="_core_output_files"></a>Fichiers de sortie

Le fichier de sortie par défaut de LINK est un fichier .exe. Si l’option [/DLL](dll-build-a-dll.md) est spécifiée, LINK construit un fichier .dll. Vous pouvez contrôler le nom de fichier de sortie avec [l’option Nom de fichier de sortie (/OUT).](out-output-file-name.md)

En mode incrémental, LINK crée un fichier .ilk pour conserver les informations d’état pour les versions progressives ultérieures du programme. Pour plus de détails sur les fichiers .ilk, voir [.ilk Files](dot-ilk-files-as-linker-input.md). Pour plus d’informations sur les liens incrémentaux, consultez l’option [Link Incrementally (/INCREMENTAL).](incremental-link-incrementally.md)

Lorsque LINK crée un programme qui contient des exportations (généralement un DLL), il construit également un fichier .lib, à moins qu’un fichier .exp a été utilisé dans la construction. Vous pouvez contrôler le nom de fichier de la bibliothèque d’importation avec l’option [/IMPLIB.](implib-name-import-library.md)

Si l’option [Generate Mapfile (/MAP)](map-generate-mapfile.md) est spécifiée, LINK crée un mapfile.

Si l’option [Generate Debug Info (/DEBUG)](debug-generate-debug-info.md) est spécifiée, LINK crée un PDB pour contenir des informations de débogage pour le programme.

## <a name="other-output"></a><a name="_core_other_output"></a>Autres sorties

Lorsque vous `link` tapez sans aucune autre entrée de ligne de commande, LINK affiche une déclaration d’utilisation qui résume ses options.

LINK affiche un message de copyright et de version et fait écho à l’entrée de fichier de commande, à moins que l’option Supprimer la [bannière de démarrage (/NOLOGO)](nologo-suppress-startup-banner-linker.md) ne soit utilisée.

Vous pouvez utiliser l’option [Messages de progrès d’impression (/VERBOSE)](verbose-print-progress-messages.md) pour afficher des détails supplémentaires sur la version.

LINK émet des messages d’erreur et d’avertissement sous la forme LNK*nnnn*. Ce préfixe d’erreur et la gamme de nombres sont également utilisés par LIB, DUMPBIN et EDITBIN.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
