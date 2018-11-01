---
title: conform
ms.date: 11/04/2016
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 6589fe23359eecd654b23380747fbd3213c54dce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432901"
---
# <a name="conform"></a>conform
**Spécifique à C++**

Spécifie le comportement au moment de l’exécution de la [/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) option du compilateur.

## <a name="syntax"></a>Syntaxe

> **#pragma conformes (** *nom* [**, afficher** ] [**,** { **sur** | **hors** }] [[**,** { **push** | **pop** }] [**,** *identificateur* ]] **)**

### <a name="parameters"></a>Paramètres

*name*<br/>
Spécifie le nom de l'option du compilateur à modifier. Valide uniquement *nom* est `forScope`.

**Show**<br/>
(Facultatif) Provoque le paramètre actuel de *nom* (true ou false) à afficher au moyen d’un message d’avertissement pendant la compilation. Par exemple, `#pragma conform(forScope, show)`.

**sur**, **désactivé**<br/>
(Facultatif) Paramètre *nom* à **sur** permet la [/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) option du compilateur. La valeur par défaut est **hors**.

**push**<br/>
(Facultatif) Exécute un push de la valeur actuelle de *nom* dans la pile interne du compilateur. Si vous spécifiez *identificateur*, vous pouvez spécifier le **sur** ou **hors** valeur pour *nom* à la pile. Par exemple, `#pragma conform(forScope, push, myname, on)`.

**pop**<br/>
(Facultatif) Définit la valeur de *nom* à la valeur en haut de la pile interne du compilateur, puis dépile la pile. Si l’identificateur est spécifié avec **pop**, la pile est alors dépilée jusqu'à ce que qu’il trouve l’enregistrement avec *identificateur*, qui sera également dépilé ; la valeur actuelle pour *nom* dans l’enregistrement suivant sur la pile devient la nouvelle valeur pour *nom*. Si vous spécifiez **pop** avec un *identificateur* qui ne se trouve pas dans un enregistrement sur la pile, le **pop** est ignoré.

*identifier*<br/>
(Facultatif) Peut être inclus avec un **push** ou **pop** commande. Si *identificateur* est utilisé, puis un **sur** ou **hors** spécificateur peut également être utilisé.

## <a name="example"></a>Exemple

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)