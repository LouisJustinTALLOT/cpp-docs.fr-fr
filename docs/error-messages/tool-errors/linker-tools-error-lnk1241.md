---
title: Erreur des LNK1241 des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1241
dev_langs:
- C++
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e4c11a97dd99515ff7623b77ff31de5fb8577b5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040620"
---
# <a name="linker-tools-error-lnk1241"></a>Erreur des outils Éditeur de liens LNK1241

fichier de ressources 'fichier de ressources' déjà spécifié

Cette erreur est générée si vous exécutez **cvtres** manuellement à partir de la ligne de commande et si vous passez le fichier .obj résultant de fichiers à l’éditeur de liens en outre d’autres fichiers .res.

Pour spécifier plusieurs fichiers .res, passez-les tous à l’éditeur de liens en tant que fichiers .res, et non depuis des fichiers .obj créés par **cvtres**.