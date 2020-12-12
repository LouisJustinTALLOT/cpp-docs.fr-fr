---
description: 'En savoir plus sur : erreur du compilateur C2696'
title: Erreur du compilateur C2696
ms.date: 11/04/2016
f1_keywords:
- C2696
helpviewer_keywords:
- C2696
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
ms.openlocfilehash: 2d4a798258ba6f9bb467c4da32e75860b96874e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326613"
---
# <a name="compiler-error-c2696"></a>Erreur du compilateur C2696

Impossible de créer un objet temporaire d’un type managé’type'

Les références à **`const`** dans un programme non managé provoquent l’appel du constructeur par le compilateur et la création d’un objet temporaire sur la pile. Toutefois, une classe managée ne peut jamais être créée sur la pile.

C2696 est accessible uniquement à l’aide de l’option de compilateur obsolète **/clr : oldSyntax**.
