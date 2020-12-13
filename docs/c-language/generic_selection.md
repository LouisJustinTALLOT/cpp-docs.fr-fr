---
title: Sélection générique (C11)
description: Décrit le mot clé de _Generic C11 utilisé dans le compilateur Microsoft Visual C
ms.date: 12/9/2020
helpviewer_keywords:
- _Generic keyword [C]
ms.openlocfilehash: de0e840c19186219d53800b9d008d7695b807bc1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97349416"
---
# <a name="generic-selection-c11"></a>Sélection générique (C11)

Utilisez le **`_Generic`** mot clé pour écrire du code qui sélectionne une expression au moment de la compilation en fonction du type de l’argument. Elle est semblable à la surcharge en C++ où le type de l’argument sélectionne la fonction à appeler, à l’exception du fait que le type de l’argument sélectionne l’expression à évaluer.

Par exemple, l’expression `_Generic(42, int: "integer", char: "character", default: "unknown");` évalue le type de `42` et recherche le type correspondant, `int` , dans la liste. Il le trouve et retourne `"integer"` .

## <a name="syntax"></a>Syntaxe

*`generic-selection`*:\
&nbsp;&nbsp;&nbsp;&nbsp;**`_Generic`** **(** *`assignment-expression`, `assoc-list`* **)**

*`assoc-list`*:\
&nbsp;&nbsp;&nbsp;&nbsp;*`association`*\
&nbsp;&nbsp;&nbsp;&nbsp;*`assoc-list`, `association`*

*`association`*:\
&nbsp;&nbsp;&nbsp;&nbsp;*`type-name`* : *`assignment-expression`*\
&nbsp;&nbsp;&nbsp;&nbsp;**`default`** : *`assignment-expression`*

La première *`assignment-expression`* est appelée expression de contrôle. Le type de l’expression de contrôle est déterminé au moment de la compilation et mis en correspondance avec le *`assoc-list`* pour Rechercher l’expression à évaluer et à retourner. L’expression de contrôle n’est pas évaluée. Par exemple, `_Generic(intFunc(), int: "integer", default: "error");` ne génère pas d’appel au moment de l’exécution `intFunc()` . 

Lorsque le type de l’expression de contrôle est déterminé, `const` ,,  `volatile` et `restrict` sont supprimés avant la correspondance *`assoc-list`* .

Les entrées du `assoc-list` qui ne sont pas choisies ne sont pas évaluées.

## <a name="constraints"></a>Contraintes

- Le *`assoc-list`* ne peut pas spécifier plusieurs fois le même type.
- Le *`assoc-list`* ne peut pas spécifier les types qui sont compatibles entre eux, par exemple une énumération et le type sous-jacent de cette énumération.
- Si une sélection générique n’a pas de valeur par défaut, l’expression de contrôle ne doit avoir qu’un seul nom de type compatible dans la liste des associations génériques.

## <a name="example"></a>Exemple

L’une des façons d’utiliser **`_Generic`** est dans une macro. Le fichier d’en-tête <tgmath. h> utilise **_Generic** pour appeler la fonction mathématique appropriée en fonction du type d’argument. Par exemple, la macro pour `cos()` mappe un appel avec un float à `cosf()` , tout en mappant un appel avec un double complexe à `ccos()` .

L’exemple suivant montre comment écrire une macro qui identifie le type de l’argument que vous lui transmettez. Elle produit `"unknown"` si aucune entrée du *`assoc-list`* correspond à l’expression de contrôle :

```C
// Compile with /std:c11

#include <stdio.h>

/* Get a type name string for the argument x */
#define TYPE_NAME(X) _Generic((X), \
      int: "int", \
      char: "char", \
      double: "double", \
      default: "unknown")

int main()
{
    printf("Type name: %s\n", TYPE_NAME(42.42));

    // The following would result in a compile error because 
    // 42.4 is a double, doesn't match anything in the list, 
    // and there is no default.
    // _Generic(42.4, int: "integer", char: "character"));
}

/* Output:
Type name: double
*/

```

## <a name="see-also"></a>Voir aussi

[`/std` (Spécifier la version du langage standard)](../build/reference/std-specify-language-standard-version.md)\
[Mathématiques de type générique](../c-runtime-library/tgmath.md)