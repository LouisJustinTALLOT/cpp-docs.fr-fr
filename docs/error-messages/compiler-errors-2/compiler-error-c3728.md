---
title: Erreur du compilateur C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165872"
---
# <a name="compiler-error-c3728"></a>Erreur du compilateur C3728

'Event' : l’événement n’a pas de méthode Raise

Les métadonnées créées avec un langage, C#telles que, qui n’autorisent pas le déclenchement d’un événement à l’extérieur de la classe dans laquelle elle a été définie, étaient incluses avec la C++ directive [#using](../../preprocessor/hash-using-directive-cpp.md) et un programme visuel utilisant la programmation CLR essayait de déclencher l’événement.

Pour déclencher un événement dans un programme développé dans un langage tel que C#, la classe contenant l’événement doit également définir une méthode publique qui déclenche l’événement.
