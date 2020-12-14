---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4622'
title: Avertissement du compilateur (niveau 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: aa7ca3f2b31f369e40b5344e008655b84b13cd1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244808"
---
# <a name="compiler-warning-level-3-c4622"></a>Avertissement du compilateur (niveau 3) C4622

Remplacement des informations de débogage formées lors de la création de l’en-tête précompilé du fichier objet : 'fichier'

Les informations CodeView dans le fichier spécifié ont été perdues lorsqu’il a été compilé avec l’option [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (utiliser des en-têtes précompilés).

Renommez le fichier objet (à l’aide de [/Fo](../../build/reference/fo-object-file-name.md)) lors de la création ou de l’utilisation du fichier d’en-tête précompilé et établissez une liaison avec le nouveau fichier objet.
