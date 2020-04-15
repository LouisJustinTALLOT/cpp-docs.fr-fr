---
title: Avertissement du compilateur (niveau 1) C4530
description: Guide de référence de l’avertissement de compilateur C4530 de Microsoft C.
ms.date: 04/02/2020
f1_keywords:
- C4530
helpviewer_keywords:
- C4530
ms.assetid: a04dcdb2-84db-459d-9e5e-4e743887465f
ms.openlocfilehash: 9de88a4b0b6c7176ff82b68c92d09d9fe75a70b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369785"
---
# <a name="compiler-warning-level-1-c4530"></a>Avertissement du compilateur (niveau 1) C4530

> Le gestionnaire d’exception de CMD utilisé, mais la sémantique décompressée n’est pas activée. Spécifier /EHsc

Le code utilise la manipulation des exceptions CMD, mais [/EHsc](../../build/reference/eh-exception-handling-model.md) n’a pas été inclus dans les options de compilateur.

## <a name="remarks"></a>Notes

Le compilateur **`/EHsc`** nécessite la possibilité de construire le code CMD qui suit la norme CMD pour la manutention des exceptions. La *sémantique de détendez-vous* standard de CMD précise que les objets et les cadres de pile construits entre l’endroit où une exception est projetée et où il est capturé doivent être détruits et leurs ressources récupérées. Ce processus est connu sous le nom *de dénouer la pile*.

L’option **`/EHsc`** indique au compilateur de générer du code qui appelle les destructeurs sur les objets de stockage automatiques lorsqu’une exception passe à travers le cadre de pile contenant. Les objets *de stockage automatiques* sont des objets répartis sur la pile, tels que les variables locales. C’est ce qu’on appelle le stockage automatique parce qu’il est alloué automatiquement lorsque les fonctions sont appelées, et libéré automatiquement quand ils reviennent. Un *cadre de pile* est les données placées sur la pile lorsqu’une fonction est appelée, avec son stockage automatique.

Lorsqu’une exception est lancée, elle peut voyager à travers plusieurs cadres de pile avant qu’elle ne soit prise. Ces cadres de pile doivent être dénoués au fur et à mesure que l’exception passe à travers eux dans l’ordre d’appel inversé. Les objets de stockage automatiques dans chaque cadre de pile doivent être détruits pour récupérer leurs ressources proprement. C’est le même processus de destruction et de récupération qui se produit automatiquement lorsqu’une fonction revient normalement.

Lorsque **`/EHsc`** l’option n’est pas activée, les objets de stockage automatiques dans les cadres de pile entre la fonction de lancer et la fonction où l’exception est capturé ne sont pas détruits. Seuls les objets de stockage automatiques créés dans un bloc **d’essai** ou **de capture** sont détruits, ce qui peut conduire à des fuites de ressources importantes et d’autres comportements inattendus.

Si aucune exception ne peut être jetée dans votre exécutable, vous pouvez ignorer cet avertissement en toute sécurité. Certains codes peuvent nécessiter d’autres options de traitement des exceptions. Pour plus d’informations, voir [/EH](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Exemple

L’échantillon suivant génère C4530 :

```cpp
// C4530.cpp
// compile with: /W1
int main() {
   try{} catch(int*) {}   // C4530
}
```

Compilez l’échantillon pour **`/EHsc`** résoudre l’avertissement.
