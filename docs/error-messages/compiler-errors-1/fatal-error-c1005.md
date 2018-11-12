---
title: Erreur irrécupérable C1005
ms.date: 11/04/2016
f1_keywords:
- C1005
helpviewer_keywords:
- C1005
ms.assetid: 150daf8e-a38a-4669-9c1a-a05b5a1f65ef
ms.openlocfilehash: a84791367656729b1cbd50ca180368f6c01531a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614459"
---
# <a name="fatal-error-c1005"></a>Erreur irrécupérable C1005

chaîne trop grande pour la mémoire tampon

Une chaîne dans un fichier intermédiaire du compilateur a entraîné un dépassement de mémoire tampon.

Vous pouvez obtenir cette erreur quand le paramètre que vous passez aux options de compilateur [/Fd](../../build/reference/fd-program-database-file-name.md) ou [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) est supérieur à 256 octets.