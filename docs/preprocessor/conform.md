---
description: 'En savoir plus sur : pragma de conformité'
title: conform, pragma
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: bb9f62194196ea32e5f3326116894ea56ef83611
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300760"
---
# <a name="conform-pragma"></a>conform, pragma

**Section spécifique à C++**

Spécifie le comportement au moment de l’exécution de l’option du compilateur [/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) .

## <a name="syntax"></a>Syntaxe

> **#pragma conforme (** *nom* [ **, affichage** ] [ **,** { **on**  |  **off** }] [[ **,** { **Push**  |  **pop** }] [ **,** *identificateur* [ **,** { **on**  |  **off** }]]] **)**

### <a name="parameters"></a>Paramètres

*nomme*\
Spécifie le nom de l'option du compilateur à modifier. Le seul *nom* valide est `forScope` .

**afficher**\
Facultatif Entraîne l’affichage du paramètre actuel de *Name* (true ou false) au moyen d’un message d’avertissement lors de la compilation. Par exemple, `#pragma conform(forScope, show)`.

**activé**, **désactivé**\
Facultatif Le  paramètre name **sur on** active l’option du compilateur [/Zc : forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . La valeur par défaut est **off**.

**souleve**\
Facultatif Exécute un push de la valeur actuelle de *Name* dans la pile interne du compilateur. Si vous spécifiez *identifier*, vous pouvez spécifier la valeur **on** ou **off** pour que *Name* fasse l’objet d’un push dans la pile. Par exemple, `#pragma conform(forScope, push, myname, on)`.

**roulant**\
Facultatif Affecte à la valeur de *Name* la valeur en haut de la pile interne du compilateur, puis dépile la pile. Si l’identificateur est spécifié avec la fonction **pop**, la pile est repilée jusqu’à ce qu’il trouve l’enregistrement avec l' *identificateur*, qui est également dépilé. la valeur actuelle de *Name* dans l’enregistrement suivant sur la pile devient la nouvelle valeur de *Name*. Si vous spécifiez **pop** avec un *identificateur* qui ne se trouve pas dans un enregistrement sur la pile, le **pop** est ignoré.

*identificateur*\
Facultatif Peut être inclus avec une commande **Push** ou **pop** . Si l' *identificateur* est utilisé, un spécificateur **on** ou **off** peut également être utilisé.

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

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
