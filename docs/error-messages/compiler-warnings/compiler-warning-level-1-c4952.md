---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4952'
title: Avertissement du compilateur (niveau 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: afbc12f6e4e8219c541acd846a3752a331abe827
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327946"
---
# <a name="compiler-warning-level-1-c4952"></a>Avertissement du compilateur (niveau 1) C4952

> '*fonction*' : aucune donnée de profil trouvée dans la base de données du programme'*pgd_file*'

Lors de l’utilisation de [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée qui a été recompilé après `/LTCG:PGINSTRUMENT` et possède une nouvelle fonction (*function*)

Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, exécutez `/LTCG:PGINSTRUMENT`, relancez toutes les séries de tests, puis exécutez `/LTCG:PGOPTIMIZE`.

Si `/LTCG:PGOPTIMIZE` avait été utilisé, cet avertissement aurait été remplacé par une erreur.
