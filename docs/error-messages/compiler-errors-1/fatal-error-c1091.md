---
title: Erreur irrécupérable C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 9758d4b779f4727012041da60632bcea8ce18d42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208531"
---
# <a name="fatal-error-c1091"></a>Erreur irrécupérable C1091

Limite du compilateur : la longueur de la chaîne dépasse de 'longueur' octets

Une constante de chaîne a dépassé la limite actuelle de longueur de chaîne.

Fractionnez la chaîne statique en deux variables (ou davantage) et utilisez [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) pour joindre le résultat dans le cadre de la déclaration ou au moment de l’exécution.