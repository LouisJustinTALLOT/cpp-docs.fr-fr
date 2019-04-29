---
title: /PDBALTPATH (Utiliser un autre chemin d’accès PDB)
ms.date: 11/04/2016
f1_keywords:
- /pdbaltpath
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
ms.openlocfilehash: 660e39a97b9fed0c5a9228fe011e7c0fa2566e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320030"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (Utiliser un autre chemin d’accès PDB)

```
/PDBALTPATH:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
Chemin d’accès et nom de fichier du fichier .pdb.

## <a name="remarks"></a>Notes

Utilisez cette option pour fournir un autre emplacement pour le fichier de base de données de programme (.pdb) dans un fichier binaire compilé. Normalement, l'éditeur de liens enregistre l'emplacement du fichier .pdb dans les binaires qu'il produit. Vous pouvez utiliser cette option pour fournir un chemin d'accès et un nom de fichier différents pour le fichier .pdb. Les informations fournies avec /PDBALTPATH ne modifient pas l'emplacement ni le nom du fichier .pdb réel. Elles modifient les informations que l'éditeur de liens écrit dans le fichier binaire. Cela vous permet de fournir un chemin d'accès indépendant de la structure de fichiers de l'ordinateur de build. Cette option a deux applications courantes : fournir un chemin d’accès réseau et fournir un fichier sans informations de chemin d’accès.

La valeur de *pdb_file_name* peut être une chaîne arbitraire, une variable d’environnement, ou **% _PDB %**. L’éditeur de liens développera une variable d’environnement, tel que **%SystemRoot%**, à sa valeur. L’éditeur de liens définit les variables d’environnement **% _PDB %** et **_EXT %**. **% _PDB %** se développe au nom de fichier du fichier .pdb réel sans informations de chemin d’accès et **_EXT %** est l’extension de fichier exécutable généré.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)<br/>
[/PDBPATH](pdbpath.md)
