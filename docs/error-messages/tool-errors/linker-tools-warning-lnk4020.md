---
title: LNK4020 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4020
dev_langs:
- C++
helpviewer_keywords:
- LNK4020
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e55239b90910f6c151949c53939d4f8ed7c15c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570685"
---
# <a name="linker-tools-warning-lnk4020"></a>Outils de l’éditeur de liens LNK4020 d’avertissement

> un enregistrement de type dans '*nom de fichier*' est endommagé ; certains symboles et types ne peuvent pas être accessibles à partir du débogueur

Le fichier PDB *nom de fichier* comporte un enregistrement de type endommagé.

Ce problème est souvent secondaire à d’autres problèmes de génération ; sauf si c’est le premier problème signalé build, traiter les autres erreurs et avertissements premier. Si c’est le premier problème signalé, vous devrez peut-être nettoyer les répertoires de votre build et régénérez votre projet. Si vous utilisez le processus de génération en parallèle, voir si l’erreur persiste lors de la sérialisation de votre build.