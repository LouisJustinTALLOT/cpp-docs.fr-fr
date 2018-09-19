---
title: Avertissement LNK4070 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4070
dev_langs:
- C++
helpviewer_keywords:
- LNK4070
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb4ae1c5440742c491d9615a2b4929a9b04f66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106942"
---
# <a name="linker-tools-warning-lnk4070"></a>Avertissement des outils Éditeur de liens LNK4070

Directive/out : filename dans. EXP diffère de nom de fichier de sortie 'nom_fichier' ; directive ignorée

Le `filename` spécifié dans le [nom](../../build/reference/name-c-cpp.md) ou [bibliothèque](../../build/reference/library.md) instruction lors de la création du fichier .exp est différente de la sortie `filename` qui était supposé par défaut ou spécifié avec le [/OUT](../../build/reference/out-output-file-name.md) option.

Vous verrez cet avertissement si vous modifiez le nom d’un fichier de sortie dans l’environnement de développement et où le fichier du projet .def n’a pas mis à jour. Mettre à jour manuellement le fichier .def pour résoudre cet avertissement.

Un programme client qui utilise la DLL résultante peut engendrer des problèmes.