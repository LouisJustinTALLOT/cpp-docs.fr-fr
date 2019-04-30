---
title: Avertissement du compilateur (niveau 1) C4182
ms.date: 11/04/2016
f1_keywords:
- C4182
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
ms.openlocfilehash: 49e3e2f62b4be50d14cb8da3d776b4640be7160c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391632"
---
# <a name="compiler-warning-level-1-c4182"></a>Avertissement du compilateur (niveau 1) C4182

\#inclure niveau d’imbrication est 'number' approfondie ; risque de récurrence infinie

Le compilateur a manqué d’espace sur le tas en raison du nombre de fichiers Include imbriqués. Un fichier Include est imbriqué quand il est inclus dans un autre fichier Include.

Ce message est un fourni à titre d’information et précède l’erreur [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).