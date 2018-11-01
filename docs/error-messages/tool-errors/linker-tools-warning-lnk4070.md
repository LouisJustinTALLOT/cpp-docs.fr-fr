---
title: Avertissement des outils Éditeur de liens LNK4070
ms.date: 11/04/2016
f1_keywords:
- LNK4070
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
ms.openlocfilehash: e7139b21f053ea8633356c7194cd719a6a4aef35
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622974"
---
# <a name="linker-tools-warning-lnk4070"></a>Avertissement des outils Éditeur de liens LNK4070

Directive/out : filename dans. EXP diffère de nom de fichier de sortie 'nom_fichier' ; directive ignorée

Le `filename` spécifié dans le [nom](../../build/reference/name-c-cpp.md) ou [bibliothèque](../../build/reference/library.md) instruction lors de la création du fichier .exp est différente de la sortie `filename` qui était supposé par défaut ou spécifié avec le [/OUT](../../build/reference/out-output-file-name.md) option.

Vous verrez cet avertissement si vous modifiez le nom d’un fichier de sortie dans l’environnement de développement et où le fichier du projet .def n’a pas mis à jour. Mettre à jour manuellement le fichier .def pour résoudre cet avertissement.

Un programme client qui utilise la DLL résultante peut engendrer des problèmes.