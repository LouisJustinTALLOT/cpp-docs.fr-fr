---
title: Avertissement des outils Éditeur de liens LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: 7810fd9a97a8f6e22ad362819a024358a9f4b07c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298579"
---
# <a name="linker-tools-warning-lnk4020"></a>Avertissement des outils Éditeur de liens LNK4020

> un enregistrement de type dans '*filename*' est endommagé ; certains symboles et types ne peuvent pas être accessibles à partir du débogueur

Le fichier PDB *filename* comporte un enregistrement de type endommagé.

Ce problème est souvent secondaire à d’autres problèmes de génération ; sauf si cela est le premier numéro de build signalé, traiter les autres erreurs et avertissements premier. Si c’est le premier problème signalé, vous devrez peut-être nettoyer les répertoires de votre build et régénérez votre projet. Si vous utilisez le processus de génération parallèle, voir si l’erreur persiste lorsque vous sérialisez votre build.