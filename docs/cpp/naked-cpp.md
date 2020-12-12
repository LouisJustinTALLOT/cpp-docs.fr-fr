---
description: 'En savoir plus sur : Naked (C++)'
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: 1f416f116d7d2a3179dc43545f1302fcd9c7d101
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313825"
---
# <a name="naked-c"></a>naked (C++)

**Spécifique à Microsoft**

Pour les fonctions déclarées avec l' **`naked`** attribut, le compilateur génère du code sans prologue ni code d’épilogue. Vous pouvez utiliser cette fonctionnalité pour écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont particulièrement utiles pour l'écriture de pilotes de périphériques virtuels.  Notez que l' **`naked`** attribut n’est valide que sur x86 et ARM, et n’est pas disponible sur x64.

## <a name="syntax"></a>Syntaxe

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Notes

Étant donné que l' **`naked`** attribut s’applique uniquement à la définition d’une fonction et n’est pas un modificateur de type, les fonctions Naked doivent utiliser la syntaxe d’attribut étendu et le mot clé [__declspec](../cpp/declspec.md) .

Le compilateur ne peut pas générer de fonction inline pour une fonction marquée avec l’attribut Naked, même si la fonction est également marquée avec le mot clé [__forceinline](inline-functions-cpp.md) .

Le compilateur émet une erreur si l' **`naked`** attribut est appliqué à un élément autre que la définition d’une méthode non membre.

## <a name="examples"></a>Exemples

Ce code définit une fonction avec l' **`naked`** attribut :

```
__declspec( naked ) int func( formal_parameters ) {}
```

Ou bien, vous pouvez également :

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

L' **`naked`** attribut affecte uniquement la nature de la génération de code du compilateur pour les séquences de prologue et d’épilogue de la fonction. Il n'affecte pas le code généré pour appeler de telles fonctions. Ainsi, l' **`naked`** attribut n’est pas considéré comme faisant partie du type de la fonction, et les pointeurs fonction ne peuvent pas avoir l' **`naked`** attribut. En outre, l' **`naked`** attribut ne peut pas être appliqué à une définition de données. Par exemple, cet exemple de code génère une erreur :

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

L' **`naked`** attribut ne s’applique qu’à la définition de la fonction et ne peut pas être spécifié dans le prototype de la fonction. Par exemple, cette déclaration génère une erreur du compilateur :

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Appels de fonction Naked](../cpp/naked-function-calls.md)
