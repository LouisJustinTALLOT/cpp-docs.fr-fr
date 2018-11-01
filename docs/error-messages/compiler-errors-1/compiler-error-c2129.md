---
title: Erreur du compilateur C2129
ms.date: 11/04/2016
f1_keywords:
- C2129
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
ms.openlocfilehash: e55107419235420d272c738e9d8ef7cf277c11c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593454"
---
# <a name="compiler-error-c2129"></a>Erreur du compilateur C2129

fonction static 'function' déclarée mais pas définie

Une référence vers l’avant est faite à un `static` fonction qui n’est jamais définie.

Un `static` fonction doit être définie au sein de la portée du fichier. Si la fonction est définie dans un autre fichier, elle doit être déclarée `extern`.