---
title: Erreur du compilateur C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 90016b65d4ddd58da3fb3c5ab6d81322dc0ef394
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566723"
---
# <a name="compiler-error-c2480"></a>Erreur du compilateur C2480

'identificateur' : 'thread' est uniquement valide pour les éléments de données d’étendue static

Vous ne pouvez pas utiliser le `thread` attribut avec une variable automatique, la donnée membre non statique, le paramètre de fonction, ou sur des définitions ou déclarations de fonction.

Utilisez le `thread` attribut pour les variables globales, les données membres statiques et les variables locales statiques uniquement.

L’exemple suivant génère l’erreur C2480 :

```
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```