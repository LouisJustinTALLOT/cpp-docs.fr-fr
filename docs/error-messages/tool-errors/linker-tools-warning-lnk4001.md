---
title: Avertissement LNK4001 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4001
dev_langs:
- C++
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f684e85233c4df777a53f03f07936137c425946e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070417"
---
# <a name="linker-tools-warning-lnk4001"></a>Avertissement des outils Éditeur de liens LNK4001

Aucun fichier objet spécifié ; bibliothèques utilisées

L’éditeur de liens a été passé à un ou plusieurs fichiers .lib, mais aucun fichier .obj.

Étant donné que l’éditeur de liens n’est pas en mesure d’accéder aux informations dans un fichier .lib qu’il est capable d’accéder à un fichier .obj, cet avertissement indique que vous devrez spécifier explicitement d’autres options de l’éditeur de liens. Par exemple, vous devrez peut-être spécifier le [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), ou [/Entry](../../build/reference/entry-entry-point-symbol.md) options.