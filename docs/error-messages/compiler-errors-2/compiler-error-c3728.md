---
title: Erreur du compilateur C3728 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e412824bd2afdadfc21d71b73f38eb8ba5ace82d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108415"
---
# <a name="compiler-error-c3728"></a>Erreur du compilateur C3728

'event' : événement n’a pas de méthode raise

Métadonnées créées avec un langage tel que c#, qui n’autorise pas un événement soit déclenché à partir en dehors de la classe dans laquelle il a été défini, ont été inclus avec le [#using](../../preprocessor/hash-using-directive-cpp.md) directive et un programme Visual C++ à l’aide de la programmation CLR essaie déclencher l’événement.

Pour déclencher un événement dans un programme développé dans un langage comme c#, la classe contenant l’événement doit également définir une méthode publique qui déclenche l’événement.