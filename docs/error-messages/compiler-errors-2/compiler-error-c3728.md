---
description: 'En savoir plus sur : erreur du compilateur C3728'
title: Erreur du compilateur C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 0cfcbd38928a153e3f5a58c1ec66b7e1c5bfd08d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245094"
---
# <a name="compiler-error-c3728"></a>Erreur du compilateur C3728

'Event' : l’événement n’a pas de méthode Raise

Les métadonnées créées avec un langage, tel que C#, qui n’autorisent pas le déclenchement d’un événement à l’extérieur de la classe dans laquelle il a été défini, étaient incluses avec la directive [#using](../../preprocessor/hash-using-directive-cpp.md) et un programme Visual C++ utilisant la programmation CLR essayait de déclencher l’événement.

Pour déclencher un événement dans un programme développé dans un langage tel que C#, la classe contenant l’événement doit également définir une méthode publique qui déclenche l’événement.
