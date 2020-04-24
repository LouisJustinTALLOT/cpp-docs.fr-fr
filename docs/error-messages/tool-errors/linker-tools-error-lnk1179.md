---
title: Erreur des outils Éditeur de liens LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: d85693cec11ef53a6bbbb60d8ced716d2a0bb131
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754334"
---
# <a name="linker-tools-error-lnk1179"></a>Erreur des outils Éditeur de liens LNK1179

Fichier invalide ou corrompu : doublement comDAT 'fichiername'

Un module d’objet contient deux COMDAT ou plus du même nom.

Cette erreur peut être causée par l’utilisation [/H](../../build/reference/h-restrict-length-of-external-names.md), qui limite la longueur des noms externes, et [/Gy](../../build/reference/gy-enable-function-level-linking.md), qui emballe fonctionne dans COMDATs.

## <a name="example"></a>Exemple

Dans le code `function1` `function2` suivant, et sont identiques dans les huit premiers caractères. La compilation avec **/Gy** et **/H8** produit une erreur de lien.

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
