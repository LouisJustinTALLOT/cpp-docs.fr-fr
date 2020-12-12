---
description: 'En savoir plus sur : erreur du compilateur C2989'
title: Erreur du compilateur C2989
ms.date: 11/04/2016
f1_keywords:
- C2989
helpviewer_keywords:
- C2989
ms.assetid: 936303d8-eb3b-4746-82ec-2f18020a6f64
ms.openlocfilehash: 38838630f5be23698de099d8c40f7e9b96bc2b13
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338605"
---
# <a name="compiler-error-c2989"></a>Erreur du compilateur C2989

'classe' : le type de classe a déjà été déclaré en tant que type non-classe

La classe générique ou le modèle redéfinit une classe non générique ou non-modèle. Recherchez les conflits dans les fichiers d’en-tête.

L’exemple suivant génère l’C2989 :

```cpp
// C2989.cpp
// compile with: /c
class C{};

template <class T>
class C{};  // C2989
class C2{};
```

C2989 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2989b.cpp
// compile with: /clr /c
ref class GC1;

generic <typename T> ref class GC1;   // C2989
template <typename T> ref class GC2;

generic <typename T> ref class GC2;   // C2989
generic <typename T> ref class GCb;
template <typename T> ref class GC2;
generic <typename T> ref class GCc;
```
