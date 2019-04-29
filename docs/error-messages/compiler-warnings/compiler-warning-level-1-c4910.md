---
title: Avertissement du compilateur (niveau 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 49cbbf3369fc4765d93e67e2dca84a4d975560d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242888"
---
# <a name="compiler-warning-level-1-c4910"></a>Avertissement du compilateur (niveau 1) C4910

'\<identificateur >' : '__declspec (dllexport)' et 'extern' sont incompatibles sur une instanciation explicite

L’instanciation de modèle explicite nommée  *\<identificateur >* est modifié à la fois par le `__declspec(dllexport)` et `extern` mots clés. Toutefois, ces mots clés s’excluent mutuellement. Le mot clé `__declspec(dllexport)` signifie que la classe de modèle doit être instanciée, tandis que le mot clé `extern` signifie que la classe de modèle ne doit pas être instanciée automatiquement.

## <a name="see-also"></a>Voir aussi

[Instanciation explicite](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Règles générales et limitations](../../cpp/general-rules-and-limitations.md)