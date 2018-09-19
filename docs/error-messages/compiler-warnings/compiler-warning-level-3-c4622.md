---
title: Compilateur avertissement (niveau 3) C4622 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4622
dev_langs:
- C++
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d91e3c914d6c3feeb9d2326c94efe2bc54ac98f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023239"
---
# <a name="compiler-warning-level-3-c4622"></a>Avertissement du compilateur (niveau 3) C4622

Remplacement des informations de débogage formées lors de la création de l’en-tête précompilé du fichier objet : 'fichier'

Les informations CodeView dans le fichier spécifié ont été perdues lorsqu’il a été compilé avec l’option [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (utiliser des en-têtes précompilés).

Renommez le fichier objet (à l’aide de [/Fo](../../build/reference/fo-object-file-name.md)) lors de la création ou de l’utilisation du fichier d’en-tête précompilé et établissez une liaison avec le nouveau fichier objet.