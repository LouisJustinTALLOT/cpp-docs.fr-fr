---
title: Erreur irrécupérable CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196545"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Erreur irrécupérable CVTRES CVT1100

Ressource dupliquée : type : type, nom : nom, langue : langue, indicateurs : indicateurs, taille : taille

La ressource donnée a été spécifiée plusieurs fois.

Vous pouvez obtenir cette erreur si l’éditeur de liens crée une bibliothèque de types et que vous n’avez pas spécifié [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) et qu’une ressource de votre projet utilise déjà 1. Dans ce cas, spécifiez/TLBID et spécifiez un autre nombre jusqu’à 65535.
