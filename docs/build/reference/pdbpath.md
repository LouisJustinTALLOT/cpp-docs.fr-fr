---
description: En savoir plus sur:/PDBPATH
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: 41207d7cfce3d72ecb9517d9ad3af8bcd3f901d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226049"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier. dll ou. exe pour lequel vous souhaitez rechercher le fichier. pdb correspondant.

**: VERBOSe**<br/>
Facultatif Signale tous les répertoires dans lesquels une tentative a été effectuée pour localiser le fichier. pdb.

## <a name="remarks"></a>Notes

/PDBPATH recherchera sur votre ordinateur les mêmes chemins que le débogueur recherchera un fichier. pdb et indiquera, le cas échéant, les fichiers. pdb correspondant au fichier spécifié dans *filename*.

Lorsque vous utilisez le débogueur Visual Studio, vous pouvez rencontrer un problème en raison du fait que le débogueur utilise un fichier. pdb pour une version différente du fichier que vous déboguez.

/PDBPATH recherche les fichiers. pdb sur les chemins d’accès suivants :

- Vérifiez l’emplacement où se trouve l’exécutable.

- Vérifiez l’emplacement du fichier PDB écrit dans l’exécutable. Il s’agit généralement de l’emplacement au moment de la liaison de l’image.

- Vérifiez le chemin de recherche configuré dans l’IDE de Visual Studio.

- Vérifiez les chemins d’accès dans les variables d’environnement _NT_SYMBOL_PATH et _NT_ALT_SYMBOL_PATH.

- Vérifiez le répertoire Windows.

## <a name="see-also"></a>Voir aussi

[Options DUMPBIN](dumpbin-options.md)<br/>
[/PDBALTPATH (utiliser un autre chemin d’accès PDB)](pdbaltpath-use-alternate-pdb-path.md)
