---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4513'
title: Avertissement du compilateur (niveau 4) C4513
ms.date: 11/04/2016
f1_keywords:
- C4513
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
ms.openlocfilehash: d9a6a0377937b3943e1c89fc41fe33abc1f6e9ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203443"
---
# <a name="compiler-warning-level-4-c4513"></a>Avertissement du compilateur (niveau 4) C4513

'classe' : impossible de générer le destructeur

Le compilateur ne peut pas générer de destructeur par défaut pour la classe donnée ; aucun destructeur n’a été créé. Le destructeur est dans une classe de base qui n’est pas accessible à la classe dérivée. Si la classe de base a un destructeur privé, rendez-le public ou protégé.
