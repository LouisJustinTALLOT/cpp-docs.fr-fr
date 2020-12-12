---
description: 'En savoir plus sur : erreur du compilateur C2480'
title: Erreur du compilateur C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 0c7f73b7e1aa205d38577602b93907309935b216
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316542"
---
# <a name="compiler-error-c2480"></a>Erreur du compilateur C2480

'identifier' : 'thread’n’est valide que pour les éléments de données d’étendue statique

Vous ne pouvez pas utiliser l' `thread` attribut avec une variable automatique, un membre de données non statique, un paramètre de fonction ou des déclarations ou définitions de fonction.

Utilisez l' `thread` attribut pour les variables globales, les données membres statiques et les variables statiques locales uniquement.

L’exemple suivant génère l’C2480 :

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
