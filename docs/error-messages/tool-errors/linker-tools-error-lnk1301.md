---
title: Erreur des outils Éditeur de liens LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: fe64eecfbc9fed57c3748afd5804b76d6e4284a4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990938"
---
# <a name="linker-tools-error-lnk1301"></a>Erreur des outils Éditeur de liens LNK1301

Modules CLR LTCG trouvés, incompatibles avec/LTCG : Parameter

Un module compilé avec/CLR et/GL a été passé à l’éditeur de liens avec l’un des paramètres d’optimisation guidée par profil (PGO) de/LTCG.

Les optimisations guidées par profil ne sont pas prises en charge pour les modules/CLR.

Pour plus d'informations, consultez .

- [/GL (Optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (Génération de code durant l’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Optimisations guidées par profil](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ne compilez pas avec/CLR ou ne liez pas l’un des paramètres PGO à/LTCG.

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK1301 :

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
