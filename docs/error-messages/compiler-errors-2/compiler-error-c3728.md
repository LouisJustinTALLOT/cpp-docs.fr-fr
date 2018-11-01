---
title: Erreur du compilateur C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454585"
---
# <a name="compiler-error-c3728"></a>Erreur du compilateur C3728

'event' : événement n’a pas de méthode raise

Métadonnées créées avec un langage tel que c#, qui n’autorise pas un événement soit déclenché à partir en dehors de la classe dans laquelle il a été défini, ont été inclus avec le [#using](../../preprocessor/hash-using-directive-cpp.md) directive et un programme Visual C++ à l’aide de la programmation CLR essaie déclencher l’événement.

Pour déclencher un événement dans un programme développé dans un langage comme c#, la classe contenant l’événement doit également définir une méthode publique qui déclenche l’événement.