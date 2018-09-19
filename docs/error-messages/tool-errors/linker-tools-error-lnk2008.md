---
title: Erreur des LNK2008 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2008
dev_langs:
- C++
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18eda06e7f133ada4de1b7ec28ac21be205a71f7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086809"
---
# <a name="linker-tools-error-lnk2008"></a>Erreur des outils Éditeur de liens LNK2008

Cible de correction n’est pas alignée 'nom_symbole'

LINK a trouvé une cible de correction dans votre fichier objet qui n’était pas correctement aligné.

Cette erreur peut être provoquée par personnalisé d’un alignement de (par exemple, #pragma [pack](../../preprocessor/pack.md)), [aligner](../../cpp/align-cpp.md) modificateur, ou à l’aide de code en langage assembleur qui modifie l’alignement.

Si votre code n’utilise aucun des éléments ci-dessus, cela peut être dû par le compilateur.