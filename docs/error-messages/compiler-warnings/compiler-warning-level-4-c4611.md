---
title: Compilateur avertissement (niveau 4) C4611 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4611
dev_langs:
- C++
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 723976dc8b7085ede9b3157445ff3026de6fc4b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091047"
---
# <a name="compiler-warning-level-4-c4611"></a>Avertissement du compilateur (niveau 4) C4611

interaction entre 'fonction' et la destruction d’objets C++ n’est pas portable

Sur certaines plateformes, les fonctions qui incluent **catch** peut prend pas en charge la sémantique d’objet C++ de destruction lorsque hors de portée.

Pour éviter un comportement inattendu, évitez d’utiliser **catch** dans les fonctions qui possèdent des constructeurs et destructeurs.

Cet avertissement est émis uniquement une seule fois ; consultez [pragma avertissement](../../preprocessor/warning.md).