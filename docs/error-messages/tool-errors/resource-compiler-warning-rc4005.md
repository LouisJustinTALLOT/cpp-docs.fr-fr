---
title: Avertissement RC4005 du compilateur de ressources | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC4005
dev_langs:
- C++
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 589fd008b3927887a8144b2fc63d2cbbde2af913
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028517"
---
# <a name="resource-compiler-warning-rc4005"></a>Avertissement RC4005 du compilateur de ressources 

'identificateur' : redéfinition de macro

L’identificateur est défini à deux reprises. Le compilateur a utilisé la deuxième définition de macro.

Cet avertissement peut être provoqué par une macro est définie sur la ligne de commande et dans le code avec un `#define` directive. Elle peut également être due par des macros importées à partir de fichiers include.

Pour éliminer l’avertissement, supprimez une des définitions ou utilisez un `#undef` directive avant la seconde définition.