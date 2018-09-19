---
title: Erreur irrécupérable C1005 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1005
dev_langs:
- C++
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 888bdaf2eaddc0d4178affa1ccc4ae77c34f4617
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092308"
---
# <a name="fatal-error-c1005"></a>Erreur irrécupérable C1005

chaîne trop grande pour la mémoire tampon

Une chaîne dans un fichier intermédiaire du compilateur a entraîné un dépassement de mémoire tampon.

Vous pouvez obtenir cette erreur quand le paramètre que vous passez aux options de compilateur [/Fd](../../build/reference/fd-program-database-file-name.md) ou [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) est supérieur à 256 octets.