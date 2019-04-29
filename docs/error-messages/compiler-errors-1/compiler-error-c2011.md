---
title: Erreur du compilateur C2011
ms.date: 11/04/2016
f1_keywords:
- C2011
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
ms.openlocfilehash: 14969c9cdf4b00844d2001bf4817ea7ffc9bfba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361553"
---
# <a name="compiler-error-c2011"></a>Erreur du compilateur C2011

'identificateur' : redéfinition du type 'type'

L'identificateur était déjà défini comme `type`. Recherchez les redéfinitions de l'identificateur.

L'erreur C2011 peut aussi apparaître si vous importez un fichier d'en-tête ou une bibliothèque de types plusieurs fois dans le même fichier. Pour empêcher plusieurs inclusions des types définis dans un fichier d’en-tête, utilisez les protections de type include ou un `#pragma` [une fois](../../preprocessor/once.md) directive dans le fichier d’en-tête.

Si vous devez rechercher la déclaration initiale du type redéfini, vous pouvez utiliser la [/P](../../build/reference/p-preprocess-to-a-file.md) indicateur de compilateur pour générer la sortie prétraitée passée au compilateur. Vous pouvez utiliser les outils de recherche de texte pour rechercher des instances de l'identificateur redéfini dans le fichier de sortie.

L'exemple suivant génère l'erreur C2011 et montre une manière de la corriger :

```
// C2011.cpp
// compile with: /c
struct S;
union S;   // C2011
union S2;   // OK
```