---
title: Erreur du compilateur C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: dc13829a267deea1f412eb2d8f86057f01dc0e1c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752416"
---
# <a name="compiler-error-c2011"></a>Erreur du compilateur C2011

'identificateur' : redéfinition du type 'type'

L'identificateur était déjà défini comme `type`. Recherchez les redéfinitions de l'identificateur.

L'erreur C2011 peut aussi apparaître si vous importez un fichier d'en-tête ou une bibliothèque de types plusieurs fois dans le même fichier. Pour empêcher plusieurs inclusions des types définis dans un fichier d’en-tête, utilisez include Guards ou une `#pragma`directive [once](../../preprocessor/once.md) dans le fichier d’en-tête.

Si vous devez rechercher la déclaration initiale du type redéfini, vous pouvez utiliser l’indicateur de compilateur [/p](../../build/reference/p-preprocess-to-a-file.md) pour générer la sortie prétraitée passée au compilateur. Vous pouvez utiliser les outils de recherche de texte pour rechercher des instances de l'identificateur redéfini dans le fichier de sortie.

L'exemple suivant génère l'erreur C2011 et montre une manière de la corriger :

```cpp
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```
