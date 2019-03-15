---
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
ms.openlocfilehash: f29b8e61fbfbdb0f373e3e7510cb3f1fe0b9cc2a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809208"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Le nom du fichier .dll ou .exe pour lequel vous souhaitez rechercher le fichier .pdb correspondant.

**:VERBOSE**<br/>
(Facultatif) Signale tous les répertoires où une tentative a été effectuée pour localiser le fichier .pdb.

## <a name="remarks"></a>Notes

/PDBPATH votre ordinateur en suivant les mêmes chemins d’accès que le débogueur pour recherche un fichier .pdb et signalera qui, le cas échéant, les fichiers .pdb correspondants dans le fichier spécifié dans *filename*.

Lorsque vous utilisez le débogueur Visual Studio, vous pouvez rencontrer un problème dû au fait que le débogueur utilise un fichier .pdb pour une autre version du fichier que vous déboguez.

/PDBPATH pour les fichiers .pdb en utilisant les chemins suivants :

- Vérifiez l’emplacement où se trouve l’exécutable.

- Vérifiez l’emplacement du fichier PDB écrit dans le fichier exécutable. Il s’agit généralement l’emplacement au moment où que l’image a été liée.

- Vérifiez le long du chemin de recherche configuré dans l’IDE Visual Studio.

- Vérifiez le long des tracés dans le _NT_SYMBOL_PATH et _NT_ALT_SYMBOL_PATH variables d’environnement.

- Vérifiez dans le répertoire Windows.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)<br/>
[/PDBALTPATH (Utiliser un autre chemin PDB)](pdbaltpath-use-alternate-pdb-path.md)
