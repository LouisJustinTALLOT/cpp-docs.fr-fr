---
description: 'En savoir plus sur : évaluateur d’expression, erreur CXX0022'
title: Évaluateur d'expression, erreur CXX0022
ms.date: 11/04/2016
f1_keywords:
- CXX0022
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
ms.openlocfilehash: e1709b371b877cb86c7874ccf006d1ad1f3238fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228117"
---
# <a name="expression-evaluator-error-cxx0022"></a>Évaluateur d'expression, erreur CXX0022

appel de fonction avant _main

L’évaluateur d’expression C ne peut pas évaluer une fonction avant que le débogueur n’ait entré la fonction **_main**. Le programme n’est pas correctement initialisé tant que **_main** n’a pas été appelé.

Cette erreur est identique à CAN0022.
