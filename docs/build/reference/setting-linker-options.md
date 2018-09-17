---
title: Définition des Options de l’éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2fd99732c7f79b3c61ff5b31516b98a478ed4a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713074"
---
# <a name="setting-linker-options"></a>Définition des options de l'Éditeur de liens

Options de l’éditeur de liens peuvent être définies à l’intérieur ou en dehors de l’environnement de développement. Cette rubrique pour chaque option de l’éditeur de liens présente comment elle peut être définie dans l’environnement de développement. Consultez [les Options de l’éditeur de liens](../../build/reference/linker-options.md) pour obtenir la liste complète.

Lorsque vous exécutez un lien en dehors de l’environnement de développement, vous pouvez spécifier l’entrée dans une ou plusieurs façons :

- Sur le [ligne de commande](../../build/reference/linker-command-line-syntax.md)

- À l’aide de [fichiers de commandes](../../build/reference/link-command-files.md)

- Dans [variables d’environnement](../../build/reference/link-environment-variables.md)

Options de processus premier lien spécifié dans la variable d’environnement LINK, suivi d’options dans l’ordre, elles sont spécifiées sur la ligne de commande et dans les fichiers de commandes. Si une option est répétée avec différents arguments, le dernier traité est prioritaire.

Options s’appliquent à la génération complète ; Aucun options ne peuvent être appliquées à des fichiers d’entrée spécifiques.

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)