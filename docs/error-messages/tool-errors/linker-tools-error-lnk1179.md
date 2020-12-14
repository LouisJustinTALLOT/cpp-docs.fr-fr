---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1179'
title: Erreur des outils Éditeur de liens LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 691476eeffadece2436518c5249ca523adca51c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253440"
---
# <a name="linker-tools-error-lnk1179"></a>Erreur des outils Éditeur de liens LNK1179

fichier non valide ou endommagé : COMDAT’nom_fichier’dupliqué

Un module objet contient au moins deux COMDAT portant le même nom.

Cette erreur peut être due à l’utilisation de [/h](../../build/reference/h-restrict-length-of-external-names.md), qui limite la longueur des noms externes, et [/Gy](../../build/reference/gy-enable-function-level-linking.md), qui empaquette les fonctions dans les COMDAT.

## <a name="example"></a>Exemple

Dans le code suivant, `function1` et `function2` sont identiques dans les huit premiers caractères. La compilation avec **/Gy** et **/H8** génère une erreur de liaison.

```cpp
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```
