---
title: Erreur du compilateur C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 340a5d0596160b6c9c7bcfc78aed812f8c5f3fa3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562866"
---
# <a name="compiler-error-c2696"></a>Erreur du compilateur C2696

Impossible de créer un objet temporaire d’un type managé 'type'

Références à `const` dans un programme non managé contraindre le compilateur à appeler le constructeur et créer un objet temporaire sur la pile. Toutefois, une classe managée ne peut jamais être créée sur la pile.

C2696 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
