---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cfe3631086515e4e31c7d4188d46e3a7440662b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177948"
---
# <a name="naked-c"></a>naked (C++)

**Section spécifique de Microsoft**

Pour les fonctions déclarées avec l’attribut **Naked** , le compilateur génère du code sans le code de prologue et d’épilogue. Vous pouvez utiliser cette fonctionnalité pour écrire vos propres séquences de code de prologue/épilogue à l'aide de code assembleur inline. Les fonctions naked sont particulièrement utiles pour l'écriture de pilotes de périphériques virtuels.  Notez que l’attribut **Naked** est uniquement valide sur x86 et ARM, et n’est pas disponible sur x64.

## <a name="syntax"></a>Syntaxe

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Notes

Étant donné que l’attribut **Naked** n’est pertinent que pour la définition d’une fonction et n’est pas un modificateur de type, les fonctions Naked doivent utiliser la syntaxe d’attribut étendu et le mot clé [__declspec](../cpp/declspec.md) .

Le compilateur ne peut pas générer de fonction inline pour une fonction marquée avec l’attribut Naked, même si la fonction est également marquée avec le mot clé [__forceinline](inline-functions-cpp.md) .

Le compilateur émet une erreur si l’attribut **Naked** est appliqué à un élément autre que la définition d’une méthode non membre.

## <a name="examples"></a>Exemples

Ce code définit une fonction avec l’attribut **Naked** :

```
__declspec( naked ) int func( formal_parameters ) {}
```

Ou bien, vous pouvez également :

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

L’attribut **Naked** affecte uniquement la nature de la génération de code du compilateur pour les séquences de prologue et d’épilogue de la fonction. Il n'affecte pas le code généré pour appeler de telles fonctions. Ainsi, l’attribut **Naked** n’est pas considéré comme faisant partie du type de la fonction, et les pointeurs fonction ne peuvent pas avoir l’attribut **Naked** . En outre, l’attribut **Naked** ne peut pas être appliqué à une définition de données. Par exemple, cet exemple de code génère une erreur :

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

L’attribut **Naked** ne s’applique qu’à la définition de la fonction et ne peut pas être spécifié dans le prototype de la fonction. Par exemple, cette déclaration génère une erreur du compilateur :

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[__declspec](../cpp/declspec.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Appels de fonction naked](../cpp/naked-function-calls.md)
