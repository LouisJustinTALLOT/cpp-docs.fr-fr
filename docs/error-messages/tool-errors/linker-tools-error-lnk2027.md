---
title: Erreur LNK2027 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 022e363af575e29e3085dcaec21257fa7e4ab5f1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116841"
---
# <a name="linker-tools-error-lnk2027"></a>Erreur des outils Éditeur de liens LNK2027

module non résolue référence 'module'

Un fichier passé à l’éditeur de liens a une dépendance sur un module qui n’était ni spécifié avec **/ASSEMBLYMODULE** ni passé directement à l’éditeur de liens.

Pour résoudre l’erreur LNK2027, effectuez l’une des opérations suivantes :

- Ne passez pas à l’éditeur de liens le fichier qui contient la dépendance de module.

- Spécifiez le module avec **/ASSEMBLYMODULE**.

- Si le module est un fichier .netmodule sécurisé, transmettez le module directement à l’éditeur de liens.

Pour plus d’informations, consultez [/ASSEMBLYMODULE (ajouter un Module MSIL à l’Assembly)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) et [fichiers .netmodule en tant qu’entrée de l’éditeur de liens](../../build/reference/netmodule-files-as-linker-input.md).