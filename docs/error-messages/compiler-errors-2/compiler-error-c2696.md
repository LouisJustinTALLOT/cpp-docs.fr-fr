---
title: Erreur du compilateur C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: f6af217dbcd871ac4edd1852042144802388545b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216087"
---
# <a name="compiler-error-c2696"></a>Erreur du compilateur C2696

Impossible de créer un objet temporaire d’un type managé’type'

Les références à **`const`** dans un programme non managé provoquent l’appel du constructeur par le compilateur et la création d’un objet temporaire sur la pile. Toutefois, une classe managée ne peut jamais être créée sur la pile.

C2696 est accessible uniquement à l’aide de l’option de compilateur obsolète **/clr : oldSyntax**.
