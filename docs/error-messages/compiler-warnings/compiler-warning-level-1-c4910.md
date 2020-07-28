---
title: Avertissement du compilateur (niveau 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: b17df9d7a9997e5d8ef37a4721de8693968cbbdf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214449"
---
# <a name="compiler-warning-level-1-c4910"></a>Avertissement du compilateur (niveau 1) C4910

' \<identifier> ' : ' __declspec (dllexport) 'et’extern’sont incompatibles sur une instanciation explicite

L’instanciation de modèle explicite nommée *\<identifier>* est modifiée par `__declspec(dllexport)` les **`extern`** Mots clés et. Toutefois, ces mots clés s’excluent mutuellement. Le `__declspec(dllexport)` mot clé signifie instancier la classe de modèle, tandis que le **`extern`** mot clé signifie que n’instancie pas automatiquement la classe de modèle.

## <a name="see-also"></a>Voir aussi

[Instanciation explicite](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Règles générales et limitations](../../cpp/general-rules-and-limitations.md)
