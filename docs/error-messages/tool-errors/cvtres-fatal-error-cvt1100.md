---
title: Erreur irrécupérable CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: c7e65ccc79852ec99dd2406398fe1b3cdecacde7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429300"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Erreur irrécupérable CVTRES CVT1100

ressource dupliquée : type : type, nom : nom, langage : langage, indicateurs : indicateurs, taille : taille

La ressource donnée a été spécifiée plusieurs fois.

Vous pouvez obtenir cette erreur si l’éditeur de liens crée une bibliothèque de types et que vous n’avez pas spécifié [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) et une ressource de votre projet utilise déjà 1. Dans ce cas, spécifiez /TLBID et spécifiez un autre numéro à 65535.