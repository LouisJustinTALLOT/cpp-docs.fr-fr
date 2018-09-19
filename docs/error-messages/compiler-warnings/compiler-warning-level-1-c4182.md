---
title: Compilateur avertissement (niveau 1) C4182 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4182
dev_langs:
- C++
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80c0cdac45238a4734b02d34f4c540c62a2f0c09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056571"
---
# <a name="compiler-warning-level-1-c4182"></a>Avertissement du compilateur (niveau 1) C4182

\#inclure niveau d’imbrication est 'number' approfondie ; risque de récurrence infinie

Le compilateur a manqué d’espace sur le tas en raison du nombre de fichiers Include imbriqués. Un fichier Include est imbriqué quand il est inclus dans un autre fichier Include.

Ce message est un fourni à titre d’information et précède l’erreur [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).