---
title: Erreur des LNK1158 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1158
dev_langs:
- C++
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce319aa4529c74cad00342b09aa0ed98bb49ce7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094167"
---
# <a name="linker-tools-error-lnk1158"></a>Erreur des outils Éditeur de liens LNK1158

Impossible d’exécuter 'nom_fichier'

Le fichier exécutable donné appelé par [lien](../../build/reference/linker-command-line-syntax.md) n’est pas dans le répertoire qui contient le lien ni dans un répertoire spécifié dans la variable d’environnement PATH.

Par exemple, vous obtiendrez cette erreur si vous essayez d’utiliser le paramètre PGOPTIMIZE le [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) option de l’éditeur de liens sur un ordinateur avec un système d’exploitation 32 bits.