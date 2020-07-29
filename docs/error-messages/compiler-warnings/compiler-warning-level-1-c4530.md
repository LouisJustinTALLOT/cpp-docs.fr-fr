---
title: Avertissement du compilateur (niveau 1) C4530
description: Guide de référence de l’avertissement du compilateur Microsoft C++ C4530.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: fe0a2b4c8eb881327f3e59d66e7e6941f0a2cad8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230660"
---
# <a name="compiler-warning-level-1-c4530"></a>Avertissement du compilateur (niveau 1) C4530

> Le gestionnaire d’exceptions C++ est utilisé, mais les sémantiques de déroulement ne sont pas activées. Spécifier/EHsc

Le code utilise la gestion des exceptions C++, mais [/EHsc](../../build/reference/eh-exception-handling-model.md) n’a pas été inclus dans les options du compilateur.

## <a name="remarks"></a>Notes

Le compilateur nécessite l' **`/EHsc`** option pour générer du code c++ qui suit la norme c++ pour la gestion des exceptions. La *sémantique de déroulement* C++ standard spécifie que les objets et les frames de pile construits entre l’emplacement où une exception est levée et celui où elle est interceptée doivent être détruits et leurs ressources récupérées. Ce processus est appelé *déroulement de la pile*.

L' **`/EHsc`** option indique au compilateur de générer le code qui appelle les destructeurs sur les objets de stockage automatique lorsqu’une exception passe par le frame de pile conteneur. Les objets de *stockage automatiques* sont des objets alloués sur la pile, tels que les variables locales. Elle est appelée stockage automatique, car elle est allouée automatiquement quand les fonctions sont appelées et libérées automatiquement quand elles retournent. Un *Frame de pile* est les données placées sur la pile lorsqu’une fonction est appelée, ainsi que son stockage automatique.

Lorsqu’une exception est levée, elle peut traverser plusieurs frames de pile avant d’être interceptée. Ces frames de pile doivent être déroulés, car l’exception les traverse dans l’ordre d’appel inverse. Les objets de stockage automatiques dans chaque frame de pile doivent être détruits pour récupérer leurs ressources correctement. Il s’agit du même processus de destruction et de récupération qui se produit automatiquement lorsqu’une fonction est retournée normalement.

Lorsque l' **`/EHsc`** option n’est pas activée, les objets de stockage automatique dans les frames de pile entre la fonction de levée et la fonction dans laquelle l’exception est interceptée ne sont pas détruits. Seuls les objets de stockage automatique créés dans **`try`** un **`catch`** bloc ou sont détruits, ce qui peut entraîner des fuites de ressources importantes et d’autres comportements inattendus.

Si aucune exception ne peut être levée dans votre exécutable, vous pouvez ignorer cet avertissement en toute sécurité. Du code peut nécessiter d’autres options de gestion des exceptions. Pour plus d’informations, consultez [/Eh](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4530 :

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compilez l’exemple avec **`/EHsc`** pour résoudre l’avertissement.
