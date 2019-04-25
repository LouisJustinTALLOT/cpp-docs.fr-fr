---
title: Erreur des outils Éditeur de liens LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: 6a82d7756f1460c56d87a3d7b1360c140de19827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160605"
---
# <a name="linker-tools-error-lnk1301"></a>Erreur des outils Éditeur de liens LNK1301

Modules clr LTCG trouvés, incompatibles avec /LTCG : paramètre

Un module compilé avec/CLR et /GL a été l’éditeur de liens avec un des optimisations guidées par profil (PGO) paramètres passé de /LTCG.

Optimisations guidées par profil ne sont pas pris en charge pour les modules / CLR.

Pour plus d'informations, voir :

- [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Génération de code durant l’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimisations guidées par profil](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ne compilez pas avec/CLR, ou ne pas lier avec l’un des paramètres PGO /LTCG.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK1301 :

```
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```