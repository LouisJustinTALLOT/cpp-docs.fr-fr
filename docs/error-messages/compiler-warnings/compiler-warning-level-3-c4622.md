---
title: Avertissement du compilateur (niveau 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 295a183afb24121a2abefd336f6ea92110220155
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185502"
---
# <a name="compiler-warning-level-3-c4622"></a>Avertissement du compilateur (niveau 3) C4622

Remplacement des informations de débogage formées lors de la création de l’en-tête précompilé du fichier objet : 'fichier'

Les informations CodeView dans le fichier spécifié ont été perdues lorsqu’il a été compilé avec l’option [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (utiliser des en-têtes précompilés).

Renommez le fichier objet (à l’aide de [/Fo](../../build/reference/fo-object-file-name.md)) lors de la création ou de l’utilisation du fichier d’en-tête précompilé et établissez une liaison avec le nouveau fichier objet.
