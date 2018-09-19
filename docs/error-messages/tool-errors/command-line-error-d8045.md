---
title: Erreur de ligne de commande D8045 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6838202178e8012df61d17e2434461d6f4858bf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022784"
---
# <a name="command-line-error-d8045"></a>Erreur de ligne de commande D8045

Impossible de compiler le fichier C 'fichier' avec l’option /clr

Uniquement les fichiers de code source C++ peuvent être passés à une compilation qui utilise **/CLR**.  Utilisez **/TP** pour compiler un fichier .c en tant que fichier .cpp ; consultez [TP, / TP, /TP (spécifier le Type des fichiers Source)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) pour plus d’informations.

Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 peut également se produire si vous compilez une application ATL à l’aide de Visual C++. Consultez [Comment : migrer vers/CLR](../../dotnet/how-to-migrate-to-clr.md) pour plus d’informations.