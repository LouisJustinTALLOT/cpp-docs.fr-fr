---
title: Avertissement des outils Éditeur de liens LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613636"
---
# <a name="linker-tools-warning-lnk4206"></a>Avertissement des outils Éditeur de liens LNK4206

> informations de type précompilé introuvable ; «*filename*' non lié ou remplacé ; objet sera lié sans informations de débogage

Le *filename* fichier objet compilé à l’aide de [/Yc](../../build/reference/yc-create-precompiled-header-file.md), n’était pas spécifié dans la commande de lien ou a été remplacé.

Un scénario courant pour cet avertissement est lorsque le fichier .obj qui a été compilé avec /Yc se trouve dans une bibliothèque, et où il n’existe aucune référence de symbole à ce fichier .obj à partir de votre code.  Dans ce cas, l’éditeur de liens ne sera pas utiliser (ou même voir) le fichier .obj.  Dans ce cas, vous devez recompiler votre code et utiliser [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pour les objets compilés à l’aide de [/Yu](../../build/reference/yu-use-precompiled-header-file.md).