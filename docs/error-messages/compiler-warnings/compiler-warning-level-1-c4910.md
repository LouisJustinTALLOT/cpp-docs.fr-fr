---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4910'
title: Avertissement du compilateur (niveau 1) C4910
ms.date: 11/04/2016
f1_keywords:
- C4910
helpviewer_keywords:
- C4910
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
ms.openlocfilehash: 4798ba8ae8005239c9cf83e109bdb0f9e4c01928
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291452"
---
# <a name="compiler-warning-level-1-c4910"></a>Avertissement du compilateur (niveau 1) C4910

' \<identifier> ' : ' __declspec (dllexport) 'et’extern’sont incompatibles sur une instanciation explicite

L’instanciation de modèle explicite nommée *\<identifier>* est modifiée par `__declspec(dllexport)` les **`extern`** Mots clés et. Toutefois, ces mots clés s’excluent mutuellement. Le `__declspec(dllexport)` mot clé signifie instancier la classe de modèle, tandis que le **`extern`** mot clé signifie que n’instancie pas automatiquement la classe de modèle.

## <a name="see-also"></a>Voir aussi

[Instanciation explicite](../../cpp/explicit-instantiation.md)<br/>
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)<br/>
[Règles générales et limitations](../../cpp/general-rules-and-limitations.md)
