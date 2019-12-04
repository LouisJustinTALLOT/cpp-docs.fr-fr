---
title: Erreur du compilateur C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743521"
---
# <a name="compiler-error-c2480"></a>Erreur du compilateur C2480

'identifier' : 'thread’n’est valide que pour les éléments de données d’étendue statique

Vous ne pouvez pas utiliser l’attribut `thread` avec une variable automatique, un membre de données non statique, un paramètre de fonction ou des définitions ou déclarations de fonction.

Utilisez l’attribut `thread` pour les variables globales, les données membres statiques et les variables statiques locales uniquement.

L’exemple suivant génère l’C2480 :

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
