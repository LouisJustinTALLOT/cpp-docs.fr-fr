---
title: Évaluateur d'expression, erreur CXX0022
ms.date: 11/04/2016
f1_keywords:
- CXX0022
helpviewer_keywords:
- CXX0022
- CAN0022
ms.assetid: f6b299ac-a4ee-492c-bd9f-6fff005bc537
ms.openlocfilehash: ac726c60d30a13d6458636d31dda6a8fb2cbd02d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359863"
---
# <a name="expression-evaluator-error-cxx0022"></a>Évaluateur d'expression, erreur CXX0022

appel de fonction avant _main

L’évaluateur d’expression C ne peut pas évaluer une fonction avant que le débogueur est passé à la fonction **_main**. Le programme n’est pas initialisé correctement jusqu'à ce que **_main** a été appelée.

Cette erreur est identique à CAN0022.