---
title: Avertissement du compilateur (niveau 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: dc5feb3613e45134a08e493b397eb738fffee8a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174776"
---
# <a name="compiler-warning-level-1-c4910"></a>Avertissement du compilateur (niveau 1) C4910

'\<identificateur > ' : ' __declspec (dllexport) 'et’extern’sont incompatibles sur une instanciation explicite

L’instanciation de modèle explicite nommée *\<identificateur >* est modifiée par les mots clés `__declspec(dllexport)` et `extern`. Toutefois, ces mots clés s’excluent mutuellement. Le mot clé `__declspec(dllexport)` signifie que la classe de modèle doit être instanciée, tandis que le mot clé `extern` signifie que la classe de modèle ne doit pas être instanciée automatiquement.

## <a name="see-also"></a>Voir aussi

[Instanciation explicite](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Règles générales et limitations](../../cpp/general-rules-and-limitations.md)
