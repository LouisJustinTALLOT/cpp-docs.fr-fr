---
description: 'En savoir plus sur : erreur du compilateur C3383'
title: Erreur du compilateur C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: fb5baf99c6738db1296cf4fb0a509c63d570ad78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285589"
---
# <a name="compiler-error-c3383"></a>Erreur du compilateur C3383

'operator new' n'est pas pris en charge avec /clr:safe

Le fichier de sortie d’une compilation **/clr:safe** est un fichier de type sécurisé vérifiable qui ne prend pas en charge les pointeurs.

Pour plus d'informations, consultez

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Problèmes courants de migration vers Visual C++ 64 bits](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3383.

```cpp
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```
