---
title: LNK4206 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.date: 12/05/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4206
dev_langs:
- C++
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cb74776f307affb0455d972e27e594e6d06294
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300870"
---
# <a name="linker-tools-warning-lnk4206"></a>Avertissement des outils Éditeur de liens LNK4206

> informations de type précompilé non trouvées ; '*nom de fichier*' non lié ou remplacé ; objet sera lié sans informations de débogage

Le *nom de fichier* fichier objet compilé à l’aide de [/Yc](../../build/reference/yc-create-precompiled-header-file.md), était soit non spécifié dans la commande LINK ou a été remplacé.

Un scénario courant pour cet avertissement est lorsque le fichier .obj qui a été compilé avec /Yc se trouve dans une bibliothèque, et où il n’existe aucune référence de symbole à ce fichier .obj à partir de votre code.  Dans ce cas, l’éditeur de liens ne sera pas utiliser (ou même voir) le fichier .obj.  Dans ce cas, vous devez recompiler votre code et utiliser [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pour les objets compilés à l’aide de [/Yu](../../build/reference/yu-use-precompiled-header-file.md).