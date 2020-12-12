---
description: 'En savoir plus sur : erreur du compilateur C3382'
title: Erreur du compilateur C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: 582a807ac43d6110fb0f19aef5806e4118516db2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285654"
---
# <a name="compiler-error-c3382"></a>Erreur du compilateur C3382

'sizeof' n'est pas pris en charge avec /clr:safe

Le fichier de sortie d’une compilation **/clr:safe** est un fichier de type sécurisé vérifiable. De plus, sizeof n’est pas pris en charge, car la valeur de retour de l’opérateur sizeof est size_t, dont la taille varie selon le système d’exploitation.

Pour plus d'informations, consultez

- [sizeof (opérateur)](../../cpp/sizeof-operator.md)

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Problèmes courants de migration vers Visual C++ 64 bits](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3382 :

```cpp
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```
