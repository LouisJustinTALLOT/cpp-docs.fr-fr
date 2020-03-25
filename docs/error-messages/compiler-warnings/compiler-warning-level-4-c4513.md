---
title: Avertissement du compilateur (niveau 4) C4513
ms.date: 11/04/2016
f1_keywords:
- C4513
helpviewer_keywords:
- C4513
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
ms.openlocfilehash: f5f25465beb04c6f91d290d4c119d07d75dd8f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185215"
---
# <a name="compiler-warning-level-4-c4513"></a>Avertissement du compilateur (niveau 4) C4513

'classe' : impossible de générer le destructeur

Le compilateur ne peut pas générer de destructeur par défaut pour la classe donnée ; aucun destructeur n’a été créé. Le destructeur est dans une classe de base qui n’est pas accessible à la classe dérivée. Si la classe de base a un destructeur privé, rendez-le public ou protégé.
