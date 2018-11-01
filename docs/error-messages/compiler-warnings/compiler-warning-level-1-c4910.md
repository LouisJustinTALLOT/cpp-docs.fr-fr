---
title: Avertissement du compilateur (niveau 1) C4910
ms.date: 11/04/2016
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: f0d1df0a383b6646d52fc2babc53ca656d49ace6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428195"
---
# <a name="compiler-warning-level-1-c4910"></a>Avertissement du compilateur (niveau 1) C4910

'\<identificateur >' : '__declspec (dllexport)' et 'extern' sont incompatibles sur une instanciation explicite

L’instanciation de modèle explicite nommée  *\<identificateur >* est modifié à la fois par le `__declspec(dllexport)` et `extern` mots clés. Toutefois, ces mots clés s’excluent mutuellement. Le mot clé `__declspec(dllexport)` signifie que la classe de modèle doit être instanciée, tandis que le mot clé `extern` signifie que la classe de modèle ne doit pas être instanciée automatiquement.

## <a name="see-also"></a>Voir aussi

[Instanciation explicite](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Règles générales et limitations](../../cpp/general-rules-and-limitations.md)