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
ms.openlocfilehash: 8323723f2049d3db469e874c91b99f4cfb561c72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439312"
---
# <a name="link-output"></a>Sortie LINK

La sortie de lien comprend des fichiers. exe, des dll, des mappage et des messages.

##  <a name="_core_output_files"></a>Fichiers de sortie

Le fichier de sortie par défaut du lien est un fichier. exe. Si l’option [/dll](dll-build-a-dll.md) est spécifiée, Link génère un fichier. dll. Vous pouvez contrôler le nom du fichier de sortie avec l’option de [nom de fichier de sortie (/out)](out-output-file-name.md) .

En mode incrémentiel, LINK crée un fichier. ilk pour contenir les informations d’État pour les générations incrémentielles ultérieures du programme. Pour plus d’informations sur les fichiers. ilk, consultez [fichiers. ilk](dot-ilk-files-as-linker-input.md). Pour plus d’informations sur les liens incrémentiels, consultez l’option [Link Incremental (/Incremental)](incremental-link-incrementally.md) .

Quand LINK crée un programme qui contient des exportations (généralement une DLL), il génère également un fichier. lib, sauf si un fichier. exp a été utilisé dans la Build. Vous pouvez contrôler le nom du fichier de bibliothèque d’importation avec l’option [/IMPLIB](implib-name-import-library.md) .

Si l’option [générer le mappage (/Map)](map-generate-mapfile.md) est spécifiée, Link crée un mappage.

Si l’option [générer des informations de débogage (/Debug)](debug-generate-debug-info.md) est spécifiée, Link crée un fichier PDB pour contenir les informations de débogage pour le programme.

##  <a name="_core_other_output"></a>Autre sortie

Lorsque vous tapez `link` sans aucune autre entrée de ligne de commande, LINK affiche une instruction d’utilisation qui résume ses options.

LIEN affiche un message de copyright et de version, et une entrée de fichier de commande Echos, sauf si l’option [Supprimer la bannière de démarrage (/nologo)](nologo-suppress-startup-banner-linker.md) est utilisée.

Vous pouvez utiliser l’option [imprimer les messages d’avancement (/verbose)](verbose-print-progress-messages.md) pour afficher des détails supplémentaires sur la Build.

LINK émet des messages d’erreur et d’avertissement sous la forme LNK*nnnn*. Ce préfixe d’erreur et cette plage de nombres sont également utilisés par LIB, DUMPBIN et EDITBIN.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
