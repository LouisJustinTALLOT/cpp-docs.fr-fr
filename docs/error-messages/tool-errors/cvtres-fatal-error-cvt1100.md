---
description: 'En savoir plus sur : CVTRES Fatal Error CVT1100'
title: Erreur irrécupérable CVTRES CVT1100
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: e54a3aeaf8b0b7955ab7e9cb7558c97a57fc95e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119734"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Erreur irrécupérable CVTRES CVT1100

Ressource dupliquée : type : type, nom : nom, langue : langue, indicateurs : indicateurs, taille : taille

La ressource donnée a été spécifiée plusieurs fois.

Vous pouvez obtenir cette erreur si l’éditeur de liens crée une bibliothèque de types et que vous n’avez pas spécifié [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) et qu’une ressource de votre projet utilise déjà 1. Dans ce cas, spécifiez/TLBID et spécifiez un autre nombre jusqu’à 65535.
