---
description: 'En savoir plus sur : erreur du compilateur C2011'
title: Erreur du compilateur C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: c310495c570a2259cf5abe6acea951ca996bfb26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221018"
---
# <a name="compiler-error-c2011"></a>Erreur du compilateur C2011

'identificateur' : redéfinition du type 'type'

L'identificateur était déjà défini comme `type`. Recherchez les redéfinitions de l'identificateur.

L'erreur C2011 peut aussi apparaître si vous importez un fichier d'en-tête ou une bibliothèque de types plusieurs fois dans le même fichier. Pour empêcher l’inclusion de plusieurs types définis dans un fichier d’en-tête, utilisez inclure des gardes ou une `#pragma` directive [once](../../preprocessor/once.md) dans le fichier d’en-tête.

Si vous devez rechercher la déclaration initiale du type redéfini, vous pouvez utiliser l’indicateur de compilateur [/p](../../build/reference/p-preprocess-to-a-file.md) pour générer la sortie prétraitée passée au compilateur. Vous pouvez utiliser les outils de recherche de texte pour rechercher des instances de l'identificateur redéfini dans le fichier de sortie.

L'exemple suivant génère l'erreur C2011 et montre une manière de la corriger :

```cpp
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```
