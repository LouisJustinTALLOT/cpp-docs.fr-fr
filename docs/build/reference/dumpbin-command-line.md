---
title: Ligne de commande DUMPBIN | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- dumpbin
dev_langs:
- C++
helpviewer_keywords:
- DUMPBIN program, command line
ms.assetid: e6ad17d3-965d-41aa-9dfd-75bb073718d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9028cebd7c75bb37bbfa958186ebb2e5d206094
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724763"
---
# <a name="dumpbin-command-line"></a>Ligne de commande DUMPBIN

Pour exécuter DUMPBIN, utilisez la syntaxe suivante :

```
DUMPBIN [options] files...
```

Spécifiez un ou plusieurs fichiers binaires, ainsi que les options requises pour contrôler les informations. DUMPBIN affiche les informations dans la sortie standard. Vous pouvez rediriger vers un fichier ou utiliser l’option /OUT pour spécifier un nom de fichier pour la sortie.

Lorsque vous exécutez DUMPBIN sur un fichier sans spécifier d’option, DUMPBIN affiche le /SUMMARY sortie.

Lorsque vous tapez la commande `dumpbin` sans aucune autre entrée de ligne de commande, DUMPBIN affiche une instruction d’utilisation qui récapitule ses options.

## <a name="see-also"></a>Voir aussi

[Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)<br/>
[Informations de référence sur DUMPBIN](../../build/reference/dumpbin-reference.md)