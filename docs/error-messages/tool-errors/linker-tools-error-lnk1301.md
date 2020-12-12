---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1301'
title: Erreur des outils Éditeur de liens LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: ac282aea62836591c6e30abb3030ef2143a78003
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335952"
---
# <a name="linker-tools-error-lnk1301"></a>Erreur des outils Éditeur de liens LNK1301

Modules CLR LTCG trouvés, incompatibles avec/LTCG : Parameter

Un module compilé avec/CLR et/GL a été passé à l’éditeur de liens avec l’un des paramètres d’optimisation guidée par profil (PGO) de/LTCG.

Les optimisations guidées par profil ne sont pas prises en charge pour les modules/CLR.

Pour plus d'informations, consultez les pages suivantes :

- [/GL (optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (génération de code durant l’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md)

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

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
