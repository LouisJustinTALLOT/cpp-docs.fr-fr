---
title: Erreur irrécupérable CVTRES CVT1100 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CVT1100
dev_langs:
- C++
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18a5508301c54637fb34a751c8f1c4e307e47d50
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068960"
---
# <a name="cvtres-fatal-error-cvt1100"></a>Erreur irrécupérable CVTRES CVT1100

ressource dupliquée : type : type, nom : nom, langage : langage, indicateurs : indicateurs, taille : taille

La ressource donnée a été spécifiée plusieurs fois.

Vous pouvez obtenir cette erreur si l’éditeur de liens crée une bibliothèque de types et que vous n’avez pas spécifié [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) et une ressource de votre projet utilise déjà 1. Dans ce cas, spécifiez /TLBID et spécifiez un autre numéro à 65535.