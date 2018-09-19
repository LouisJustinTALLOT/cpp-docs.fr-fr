---
title: Avertissement LNK4010 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4010
dev_langs:
- C++
helpviewer_keywords:
- LNK4010
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e214f603c31c72533d81a140023363880532191c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068065"
---
# <a name="linker-tools-warning-lnk4010"></a>Avertissement des outils Éditeur de liens LNK4010

numéro de numéro de version de sous-système non valide ; version de sous-système par défaut prise par défaut

Vous pouvez spécifier une version pour le sous-système de l’image ([/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)). Chaque sous-système a une version minimale requise. Si la version spécifiée est inférieure à la valeur minimale, cet avertissement se produit et l’éditeur de liens utilise simplement le sous-système par défaut.