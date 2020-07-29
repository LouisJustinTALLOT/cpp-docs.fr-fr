---
title: __assume
ms.date: 09/02/2019
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: 80acb417ed85ced8f72906848474837efe6bc9d1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225096"
---
# <a name="__assume"></a>__assume

**Spécifique à Microsoft**

Passe une indication à l'optimiseur.

## <a name="syntax"></a>Syntaxe

```C
__assume(
   expression
)
```

### <a name="parameters"></a>Paramètres

*formule*\
Toute expression supposée être évaluée à True.

## <a name="remarks"></a>Notes

L'optimiseur part du principe que la condition représentée par `expression` est remplie au point où le mot clé apparaît et le reste jusqu'à ce qu'`expression` soit modifiée (par exemple, par assignation à une variable). L’utilisation sélective des indicateurs passés à l’optimiseur par **`__assume`** peut améliorer l’optimisation.

Si l' **`__assume`** instruction est écrite comme une contradiction (une expression qui prend toujours la valeur false), elle est toujours traitée comme `__assume(0)` . Si votre code ne se comporte pas comme prévu, assurez-vous que l'`expression` que vous avez définie est valide et a la valeur True, comme indiqué plus haut. Pour plus d'informations sur le comportement attendu de `__assume(0)`, consultez les notes plus loin dans cet article.

> [!WARNING]
> Un programme ne doit pas contenir d' **`__assume`** instruction non valide sur un chemin d’accès accessible. Si le compilateur peut atteindre une instruction non valide **`__assume`** , le programme peut provoquer un comportement imprévisible et potentiellement dangereux.

`__assume` n'est pas une véritable intrinsèque. Vous n'êtes pas obligé de la déclarer en tant que fonction et vous ne pouvez pas l'utiliser dans une directive `#pragma intrinsic`. Bien qu'aucun code ne soit généré, le code généré par l'optimiseur est affecté.

Utilisez **`__assume`** dans une [assertion](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) uniquement lorsque l’assertion n’est pas récupérable. N’utilisez pas **`__assume`** dans une assertion pour laquelle vous avez un code de récupération d’erreur ultérieur, car le compilateur peut optimiser le code de gestion des erreurs.

L'instruction `__assume(0)` est un cas spécial. Utilisez `__assume(0)` pour indiquer un chemin d'accès de code qui ne peut pas être atteint. L'exemple suivant montre comment utiliser `__assume(0)` pour indiquer que le cas par défaut d'une instruction switch ne peut pas être atteint. Il illustre l'utilisation la plus courante de `__assume(0)`.

Pour la compatibilité avec les versions précédentes, **`_assume`** est un synonyme de, **`__assume`** sauf si l’option de compilateur [/za \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|**`__assume`**|x86, ARM, x64, ARM64|

## <a name="example"></a>Exemple

```cpp
// compiler_intrinsics__assume.cpp
#ifdef DEBUG
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )
#else
# define ASSERT(e)    ( __assume(e) )
#endif

void func1(int i)
{
}

int main(int p)
{
   switch(p){
      case 1:
         func1(1);
         break;
      case 2:
         func1(-1);
         break;
      default:
         __assume(0);
            // This tells the optimizer that the default
            // cannot be reached. As so, it does not have to generate
            // the extra code to check that 'p' has a value
            // not represented by a case arm. This makes the switch
            // run faster.
   }
}
```

L'utilisation de `__assume(0)` indique à l'optimiseur que le cas par défaut ne peut pas être atteint. L'exemple montre que le programmeur sait que les seules entrées possibles pour `p` seront 1 ou 2. Si une autre valeur est passée pour `p`, le programme n'est plus valide et provoque un comportement imprévisible.

Suite à l'instruction `__assume(0)`, le compilateur ne génère pas de code pour vérifier si `p` a une valeur qui n'est pas représentée dans une instruction Case. Pour que cela fonctionne, l'instruction `__assume(0)` doit être la première instruction dans le corps du cas par défaut.

Étant donné que le compilateur génère du code basé sur **`__assume`** , ce code risque de ne pas s’exécuter correctement si l’expression à l’intérieur de l' **`__assume`** instruction a la valeur false au moment de l’exécution. Si vous n'êtes pas sûr que l'expression sera toujours True au moment de l'exécution, vous pouvez utiliser la fonction `assert` pour protéger le code.

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Malheureusement, cette utilisation d'`assert` empêche le compilateur d'effectuer l'optimisation de cas par défaut décrite plus haut dans ce document. En guise d'alternative, vous pouvez utiliser une macro distincte, comme suit.

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[Mots clés](../cpp/keywords-cpp.md)
