---
title: Erreur des outils Éditeur de liens LNK2008
ms.date: 11/04/2016
f1_keywords:
- LNK2008
helpviewer_keywords:
- LNK2008
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
ms.openlocfilehash: c7794d09f7eeb9dceba7098ca7af90ccf2eeccad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194822"
---
# <a name="linker-tools-error-lnk2008"></a>Erreur des outils Éditeur de liens LNK2008

Cible de correction non alignée’symbol_name'

Un lien a trouvé une cible de correction dans votre fichier objet qui n’a pas été correctement alignée.

Cette erreur peut être due à un alignement Secton personnalisé (par exemple, #pragma [Pack](../../preprocessor/pack.md)), à un modificateur d' [alignement](../../cpp/align-cpp.md) ou à l’utilisation d’un code de langage assembleur qui modifie l’alignement de Secton.

Si votre code n’utilise pas l’un des éléments ci-dessus, cela peut être dû au compilateur.
