---
title: Avertissement du compilateur C4962
ms.date: 11/04/2016
f1_keywords:
- C4962
helpviewer_keywords:
- C4962
ms.assetid: 62b156fe-04e5-4a6e-9339-6ab148185f87
ms.openlocfilehash: e3f7b715da3774d8289fdd526cf1fa0b5bdddba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585313"
---
# <a name="compiler-warning-c4962"></a>Avertissement du compilateur C4962

'fonction' : les optimisations guidées par profil sont désactivées, car elles génèrent des incohérences au niveau des données de profil

Une fonction n’a pas été compilée avec /LTCG:PGO, car les données de décompte (profil) pour la fonction n’étaient pas fiables. Réexécutez le profilage pour régénérer le fichier .pgc qui contient les données de profil non fiables pour cette fonction.

Cet avertissement est désactivé par défaut. Pour plus d'informations, consultez [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).