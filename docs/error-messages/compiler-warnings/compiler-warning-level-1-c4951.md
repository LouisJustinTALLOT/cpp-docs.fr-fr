---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4951'
title: Avertissement du compilateur (niveau 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: effb1f5af0c406de002b5c0b8522e7c58a2424a5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327966"
---
# <a name="compiler-warning-level-1-c4951"></a>Avertissement du compilateur (niveau 1) C4951

> '*Function*'a été modifié depuis que les données de profil ont été collectées, données de profil de fonction non utilisées

Une fonction d’un module d’entrée a été remplacée par [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de sorte que les données de profil ne sont plus valides. Le module d’entrée a été recompilé après **/LTCG:PGINSTRUMENT** et a une fonction (*function*) avec un flux de contrôle différent de celui du module au moment de l’opération **/LTCG:PGINSTRUMENT** .

Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, exécutez **/LTCG:PGINSTRUMENT**, relancez toutes les séries de tests, puis exécutez **/LTCG:PGOPTIMIZE**.

Si **/LTCG:PGOPTIMIZE** avait été utilisé, cet avertissement aurait été remplacé par une erreur.
