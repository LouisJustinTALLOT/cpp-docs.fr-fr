---
title: Avertissement LNK4020 des outils de l’éditeur de liens
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609740"
---
# <a name="linker-tools-warning-lnk4020"></a>Avertissement LNK4020 des outils de l’éditeur de liens

> un enregistrement de type dans '*filename*' est endommagé ; certains symboles et types ne peuvent pas être accessibles à partir du débogueur

Le fichier PDB *filename* comporte un enregistrement de type endommagé.

Ce problème est souvent secondaire à d’autres problèmes de génération ; sauf si cela est le premier numéro de build signalé, traiter les autres erreurs et avertissements premier. Si c’est le premier problème signalé, vous devrez peut-être nettoyer les répertoires de votre build et régénérez votre projet. Si vous utilisez le processus de génération parallèle, voir si l’erreur persiste lorsque vous sérialisez votre build.