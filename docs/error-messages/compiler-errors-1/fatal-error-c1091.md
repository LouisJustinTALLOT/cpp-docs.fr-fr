---
title: Erreur irrécupérable C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 76492be7abab6deb740f1670b85274b8c296c783
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203890"
---
# <a name="fatal-error-c1091"></a>Erreur irrécupérable C1091

Limite du compilateur : la longueur de la chaîne dépasse de 'longueur' octets

Une constante de chaîne a dépassé la limite actuelle de longueur de chaîne.

Fractionnez la chaîne statique en deux variables (ou davantage) et utilisez [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) pour joindre le résultat dans le cadre de la déclaration ou au moment de l’exécution.
