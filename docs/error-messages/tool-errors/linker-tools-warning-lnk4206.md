---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4206'
title: Avertissement des outils Éditeur de liens LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: 40d7a8f18a835721ff747293696d0499c0a94ef3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294143"
---
# <a name="linker-tools-warning-lnk4206"></a>Avertissement des outils Éditeur de liens LNK4206

> informations de type précompilé introuvables ; '*nom_fichier*'n’est pas lié ou remplacé ; liaison de l’objet comme si aucune information de débogage

Le fichier objet *filename* , compilé à l’aide de [/Yc](../../build/reference/yc-create-precompiled-header-file.md), n’a pas été spécifié dans la commande LINK ou a été remplacé.

Un scénario courant pour cet avertissement est lorsque le. obj qui a été compilé avec/Yc se trouve dans une bibliothèque et lorsqu’il n’existe aucune référence de symbole à ce. obj à partir de votre code.  Dans ce cas, l’éditeur de liens n’utilise pas (ou ne peut même pas voir) le fichier. obj.  Dans ce cas, vous devez recompiler votre code et utiliser [/yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pour les objets compilés à l’aide de [/Yu](../../build/reference/yu-use-precompiled-header-file.md).
