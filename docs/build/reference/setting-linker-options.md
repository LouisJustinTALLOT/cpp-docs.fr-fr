---
title: Définition des options de l'Éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- input files [C++], linker
- linker [C++], ways to set options
- linker [C++], switches
- input files [C++]
- object/library modules
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
ms.openlocfilehash: 61f4ee8d02cda5b2cd270d7ef789bf58060e7fdf
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423168"
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
