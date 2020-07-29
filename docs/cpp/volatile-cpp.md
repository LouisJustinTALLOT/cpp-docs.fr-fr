---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: bbdd7d03d820b9fc0d541dbb31d55b641226f14e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213097"
---
# <a name="volatile-c"></a>volatile (C++)

Qualificateur de type que vous pouvez utiliser pour déclarer qu'un objet peut être modifié dans le programme par le matériel.

## <a name="syntax"></a>Syntaxe

```
volatile declarator ;
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser le commutateur de compilateur [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) pour modifier la façon dont le compilateur interprète ce mot clé.

Visual Studio interprète le **`volatile`** mot clé différemment en fonction de l’architecture cible. Pour ARM, si aucune option de compilateur **/volatile** n’est spécifiée, le compilateur exécute comme si **/volatile : ISO** était spécifié. Pour les architectures autres que ARM, si aucune option de compilateur **/volatile** n’est spécifiée, le compilateur exécute comme si **/volatile : ms** était spécifié ; par conséquent, pour les architectures autres que ARM, nous vous recommandons vivement de spécifier **/volatile : ISO**, et d’utiliser des primitives de synchronisation explicites et des intrinsèques du compilateur lorsque vous traitez une mémoire partagée entre les threads.

Vous pouvez utiliser le **`volatile`** qualificateur pour fournir l’accès aux emplacements de mémoire utilisés par les processus asynchrones, tels que les gestionnaires d’interruption.

Lorsque **`volatile`** est utilisé sur une variable qui possède également le mot clé [__restrict](../cpp/extension-restrict.md) , est **`volatile`** prioritaire.

Si un **`struct`** membre est marqué comme **`volatile`** , **`volatile`** est propagé à la structure entière. Si une structure n’a pas de longueur pouvant être copiée sur l’architecture actuelle à l’aide d’une instruction, **`volatile`** peut être complètement perdu sur cette structure.

Le **`volatile`** mot clé peut n’avoir aucun effet sur un champ si l’une des conditions suivantes est vraie :

- La longueur du champ volatile dépasse la taille maximale pouvant être copiée sur l'architecture actuelle en utilisant une instruction.

- La longueur de l’extérieur contenant **`struct`** , ou s’il s’agit d’un membre d’un éventuellement imbriqué **`struct`** , dépasse la taille maximale pouvant être copiée sur l’architecture actuelle en utilisant une instruction.

Bien que le processeur ne réorganise pas les accès à la mémoire qui ne sont pas mis en cache, les variables qui ne sont pas mises en cache doivent être marquées comme **`volatile`** pour garantir que le compilateur ne réorganise pas les accès à la mémoire.

Les objets déclarés comme ne **`volatile`** sont pas utilisés dans certaines optimisations, car leurs valeurs peuvent changer à tout moment.  Le système lit toujours la valeur actuelle d'un objet volatile lorsque la demande en est faite, même si une instruction précédente a demandé une valeur du même objet.  De même, la valeur de l'objet est écrite immédiatement sur l'assignation.

## <a name="iso-compliant"></a>Conformité ISO

Si vous êtes familiarisé avec le mot clé volatile C# ou si vous connaissez le comportement de **`volatile`** dans les versions antérieures du compilateur Microsoft c++ (MSVC), sachez que le mot clé standard ISO C++ 11 **`volatile`** est différent et est pris en charge dans MSVC lorsque l’option de compilateur [/volatile : ISO](../build/reference/volatile-volatile-keyword-interpretation.md) est spécifiée. (Pour ARM, elle est spécifiée par défaut). Le **`volatile`** mot clé en code standard ISO 11 est utilisé uniquement pour l’accès au matériel ; ne l’utilisez pas pour la communication entre threads. Pour la communication entre threads, utilisez des mécanismes tels que [std : \<T> : Atomic](../standard-library/atomic.md) à partir de la [bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Fin de la conformité ISO

**Spécifique à Microsoft**

Lorsque l’option **/volatile : ms** du compilateur est utilisée, par défaut lorsque des architectures autres que ARM sont ciblées, le compilateur génère du code supplémentaire pour conserver l’ordre des références aux objets volatiles, en plus de la gestion des références à d’autres objets globaux. En particulier :

- L’écriture dans un objet volatile (également appelée "écriture volatile") a une sémantique Release, c’est-à-dire, une référence à un objet global ou statique qui se produit avant qu’une écriture dans un objet volatile de la séquence d’instructions ne se produise avant cette écriture volatile dans le fichier binaire compilé.

- La lecture d'un objet volatile (également appelée "lecture volatile") a une sémantique Acquire, c'est-à-dire, une référence à un objet global ou statique qui se produit après qu'une lecture de la mémoire volatile dans la séquence d'instructions se produit après cette lecture volatile dans le fichier binaire compilé.

Cela permet aux objets volatiles d'être utilisés pour les verrous et les libérations de mémoire dans les applications multithread.

> [!NOTE]
> Lorsqu’il s’appuie sur la garantie améliorée fournie quand l’option de compilateur **/volatile : ms** est utilisée, le code n’est pas portable.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Pointeurs const et volatile](../cpp/const-and-volatile-pointers.md)
